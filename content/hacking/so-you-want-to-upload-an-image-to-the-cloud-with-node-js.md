Title: So you want to upload an image to the cloud with Node.js
Date: 2016-11-15 21:17
Author: max
Category: hacking
Slug: so-you-want-to-upload-an-image-to-the-cloud-with-node-js
Status: published

So you want to upload an image to the cloud with Node.js?
---------------------------------------------------------

Maybe you want a small raspberry pi webcam to take timelapse footage and send it to a server every hour because of its small harddrive. Maybe you want to build a social network swapping images of Lizard People, and your sever can t handle all the image traffic. Maybe you want to back-up your irreplaceable collection of dead-sea scroll fragments -- it's irreplaceable. You  might want to keep around images or files for many different reasons, and having them publicly accessible in the cloud is better than trying to manage them yourself, for storage and network reasons. This is a tutorial about how to do that. In this tutorial we will be building and inspecting a use case for a web-app I've been working on in which users can post images of items they want to trade.

Just focusing on the backend, we'll be assuming there's already webpage with a file upload user-interface. What we'll be doing is creating the API endpoint that images can be uploaded to, but will then turn-around and ask a cloud-strorage provider to hold the image for us. We'll also make a square thumbnail version of the image and upload those too. Once both of these images (the full-size and the thumbnail) are in the cloud, we'll return to the web-client a URL of where the images can be found in the cloud.

![Architectural Overview]({static}/images/uploads/2016/11/Untitled-drawing1.png){.aligncenter .size-full .wp-image-4110 style="width:958px !important"}

Choices, choices
----------------

Let's take a moment to justify the technologies we are using. The first is node.js. There's a Ph.D. student who works at my university researching programming languages who starts all of his presentations with the question: "why on earth does anyone write in node.js?" It's funny the first few times you hear it, and if you're like me who fell in love with python, you might be reticent. But there is some justification here, although some of our processing needs to happen synchronously, but a lot doesn't, so nodeJS's asynchronous-by-default nature will be useful.

The next question we have to answer is, which cloud storage provider to use. I investigated a couple of candidates, and eventually settled on using Microsoft's Azure, because it came with some excellent sample applications and code that made it easy to get off the ground in an hour. It's not the only one out there though, I also thought about Amazon S3 the popular giant - but its popular enough already. I looked at Google Cloud Services, which does come with node.js wrappers which is nice, but I didn't see any sample applications so it wasn't as dev-friendly as it could have been. I also wanted to consider companies that weren't corporations of sizes I can't even fathom, so I poked around Rackspace's promising offerings, but their documentation was written entirely in cURL exmaples, and we're trying to play this game on easy mode. Lastly, Cloudinary seems like a good service which is more purpose-build for images, not just general storage, and so has a built-in thumbnail API. I wish my colleague had told me about Cloudinary before I'd written this tutorial not after, it may have come out differently.

One last thing to note is how much these services cost, what I noticed is that their pricing structures were more similar than different. \$0.003 per GB of traffic matters to Netflix, not to us for these purposes.

  ----------------------- ---------------------------------------------------------------------
  Amazon S3               The popular leader in cloud storage. Yawn.
  Google Cloud Services   Node.js library, no example application
  Rackspace               Thoughtful company, documentation is cURL only, no node.js library.
  Azure                    Node.js library and example applications.
  Cloudinary               Potentially interesting entrant, which image-focused features.
  ----------------------- ---------------------------------------------------------------------

Set up
------

For this toturial you'll need a Microsoft Azure account. They'll give you \$200 free credit to start off, so go sign-up at [http://portal.azure.com/](http://portal.azure.com) without entering a credit card, and setup your "Blob" storage.

![Make a new Storage Account]({static}/images/uploads/2016/11/azure1.png){.size-full .wp-image-4112 style="width:726px !important"} Make a new Storage Account

Remember these credentials for your application. When everything is set up you'll see your container like this:

![There can be many containers, which contain blobs. Each blob has a deterministic URL. Note, the Key icon which contains your secret key needed for later on.]({static}/images/uploads/2016/11/azure3.png){.size-large .wp-image-4113 style="width:474px !important"} There can be many containers, which contain blobs. Each blob has a deterministic URL. Note, the Key icon which contains your secret key needed for later on.

Now we'll move on to getting our node.js enviorment set up. With the magic of `npm` this is remarkably easy. In your project folder do

``` {.EnlighterJSRAW enlighter-language="shell"}
npm install azure-storage --save
```

As I mentioned Azure's storage solution not only has a node.js library, but also comes with a nice simple [sample application](https://github.com/Azure/azure-sdk-for-node/blob/c98fd8ff9310f688a7ff6a227015876cd1f722ab/examples/ASM/samples/continuationsample.js) which I'll embellish and go over in more detail.

Breaking the Code
-----------------

We're ready to look at some code. What you're about to see is inside an [express application](http://expressjs.com/) which I won't cover now. If you're not familiar with express it's quite easy to pick up, but for now pay attention to the broad strokes.

``` {.EnlighterJSRAW}
var azure = require('azure-storage');
var formidable = require('formidable');
//for parsing data that comes with our images
var lwip = require('lwip');
//to make our thumbnails
const storageAccount = 'youenteredthisatazureportal'
const storageAccessKey = 'alongrandomstringyougetfromazure'
const azureEndpoint = 'https://OURDOMAIN.blob.core.windows.net/'
const containerName = 'youenteredthisatazureportal';

var blobClient = azure.createBlobService(storageAccount, storageAccessKey);
```

We now have the the blobClient which is an Object that has a method which will accept our image and upload it, keep this in mind. Next we'll plumb in our API to respond to HTTP POST requests at `/uploadhandler`.

``` {.EnlighterJSRAW enlighter-language="null"}
router.post('/uploadhandler', function (req, res) {
  var form = new formidable.IncomingForm();
  var itemId = new Date().getTime()
  form.parse(req, function (err, fields, files) {
      var options = {
        contentType: 'image/jpeg',
        metadata: {fileName: itemId}
        }
      var imgPath = files.image.path
      var machineId = fields.machineId
      var userName = fields.userName
      makeThumb(imgPath, itemId, machineId, userName, options, res, uploadThumb);
      uploadFull(imgPath, itemId, options)
  });
});
```

In this example we are expecting a `form`  which contains our image in the `files.image` attribute, and some other data like `machineId` and `userName` which came along for the ride in fields of the form. After that's all parsed, we are going to make a thumb, and we're sending it the callback `uploadThumb` to run afterwards. `uploadFull` doesn't need any preprocessing so we can send it on it's merry way right now, giving it the image path and an `itemId` which basically serves as a unique-enough-for-now name for our file. We also are giving Azure some clues as to what this data is that we're sending it in the  `options` object. For simplicity we're assuming its a jpeg.

I bet you're wondering what those upload functions do?

``` {.EnlighterJSRAW enlighter-language="null"}
var uploadFull = function(imgPath, itemId, options){
  var fileName = itemId + '.jpg'
  blobClient.createBlockBlobFromLocalFile(containerName, fileName, imgPath, options, function (error) {
    if (error != null) {
      console.log('Azure Full Error: ', error)
    } else {
      console.log('Azure Full Success')
    }
  });
}
```

`uploadFull` is going take our image file and plug it into the blobClient's `createBlockBlobFromLocalFile` method. It takes a callback to know how to handle errors. Actually this a weak point of Azure that I'll cover later, about why what arguments passed to this callback are insufficient. But lets take a moment here some magic happened. blobClient is abstracting away a lot of HTTP-based complexity for us--thanks Azure SDK.

Now let's see how to make make a square thumbnail out of our image, and at the same time uncover a gripe I have about azure's SDK.

``` {.EnlighterJSRAW enlighter-language="null"}
var makeThumb = function(imgPath, itemId, machineId, userName, options, res, callback){
  lwip.open(imgPath, 'jpg', function(err, image){
    image.cover(320, 320, function(err, image){
      image.toBuffer('jpg', function(err, buffer){
        callback(buffer, itemId, machineId, userName, options, res)
      });
    });
  });
};
```

We use the aptly named ["LightWeight Image Processing" library](https://github.com/EyalAr/lwip) , to make a 320x320 pixel thumbnail. There is actually a single call that will do this in `image.cover` . But notice that we passed in a string representing a path and what we got back was a buffer. We could have saved the image as a file, but what's the point in cloud upload if you're going to save the files locally?

At this point we have an image as a buffer and we want to push this to Azure too.

``` {.EnlighterJSRAW enlighter-language="null"}
var uploadThumb = function(buffer, itemId, machineId, userName, options, res){
  var fileName = itemId + '_thumb.jpg'
  blobClient.createBlockBlobFromText(containerName, fileName, buffer, options, function (error) {
    if (error != null) {
      console.log('Azure Thumb Error: ', error)
      res.send({sucess:false})
    } else {
      console.log('Azure Thumb Success')
      anItem = {itemid: itemId,
               machineid:machineId,
               label:'Unlabeled',
               username:userName
               thumbURL:azureEndpoint+fileName}
      res.send({success:true, item:anItem});
    }
  });
};
```

Luckily blobClient has another method `createBlockBlobFromText` which can handle this buffer and work its magic again. Finally if we get success back from the thumbnail upload, we can tell that `res` response object we've been passing around to send some metadata back to the client, so they can know what happened to their image upload. They can use the `thumbURL` attribute to know where to look for a thumbnail online.  And we're done. QED.

Discussion
----------

Azure's SDK made our image uploading easy, but with close analysis there is a some room for improvement. The first thing to notice, which is mentioned earlier is that the callback that the blobClient methods require is one that takes `err` as its only argument. I would feel better about my life is they would also send back some data about where the blob got stored. It's true that you can piece it together because it *should* be at `azureEndpoint+fileName`, but I would have more (ahem) piece of mind if it returned this URL to me.

The real annoyance is that blobClient has two separate methods for dealing with file paths and text buffers. One method that could either infer these two cases, or provide a specifier as an optional argument makes more sense to me. If it were so, it would allow us more easily to write higher-level functions using the blobClient for many different operations.

Conclusion
----------

I hope you learned to node, to upload, and to Azure for great good.  This sketch walked us through making an account with Azure and then linking in the Azure SDK with Express. They have many good [resources themselves at Microsoft Developer Network](https://docs.microsoft.com/en-us/azure/storage/storage-nodejs-how-to-use-blob-storage). Without confusion, signing off.
