Title: How A Small Bug I Wrote Started Helping Holocaust Deniers
Date: 2016-05-02 02:13
Author: max
Category: blog
Slug: how-a-small-bug-i-wrote-started-helping-holocaust-deniers
Status: published

In my early software education, I'd been taught about how [untested  software could result in deadly radiation-therapy machines.](https://en.wikipedia.org/wiki/Therac-25) But since I never planned to be in the medical devices industry, these sort of warnings didn't apply to me - after all I was only writing Wikipedia bots. But this week I was proved wrong when another Wikipedian messaged me with a query unlike any I'd received before (empahsis mine):

> Hi Max, I've pinged you a couple of times, but in case you're not getting them, would you mind commenting?
>
> It's about an edit your bot made to Wikidata that changed the infobox of a featured article about a book about the Holocaust, [Night](https://en.wikipedia.org/wiki/Night_%28book%29 "Night (book)"). The bot fetched data from the Italian Wikipedia, rather than from the English (the book is in English) or the French (it was first published in France).
>
> The issue is that the Italian Wikipedia calls it fiction (a novel), rather than memoir. This is an issue because Holocaust deniers call it fiction too, so we've avoided doing the same. It's not that only Holcaust deniers call it that (it is memoir, but parts appear to have been fictionalized, so "novel" is not a horrible genre for it), but there is sensitivity around it because of them, and the author doesn't like it to be called a novel.
>
> I'm trying to find out why your bot would have fetched the data from the Italian Wikipedia. Any light you can shed on it would be appreciated. Best wishes, [SarahSV](https://en.wikipedia.org/wiki/User:SlimVirgin "User:SlimVirgin") [[(talk)](https://en.wikipedia.org/wiki/User_talk:SlimVirgin "User talk:SlimVirgin")] 02:12, 29 April 2016 (UTC)

The truth is that this was an honest mistake because my intention, in line with the philosophical underpinnings of Wikidata is to avoid this sort of cross-cultural conflict. Wikidata has a pluralist ideology, that is it can support many competing facts without favouring any one. It allows you to say that the book Night is: a novel (according to these historians), and separately an autobiography (according to some other source). My intention was to use this pluralist structure, with the sources being Italian and English Wikipedias, but a bug in my code prevented that ideal.  (By the way I believe the Holocaust did happen, [read about my ancestral trip to Poland to find out more](http://notconfusing.com/kleins-search-for-klajnbohms-an-ancestral-research-trip-to-zwolen-poland).)

Basically, the technical issue was that I missed an 'else' case because of a poor programming design. In some cases just the first Wikipedia languages I was inspecting would be represented in Wikidata. I was utilizing English, German, French, Spanish, Italian, Japanese, Russian, Polish, Swedish Wikipedias, in no particular order, and in this case Italian went first, and only it's opinion about the genre of Night, was carried into Wikidata.

I now feel and understand empirically why testing so is crucial. It's no longer and abstract, academic curiosity backed up thinly by seemingly unrelated horror stories. Thank you life for teaching me this lesson. And perhaps, as my colleagues have commented, the way algorithms - and all their shortcomings - shape history, is a rich venue for research.

Interested programmers may read on for details of the bug. [Looking at my old code](https://gist.github.com/notconfusing/0dfed7e9bea694ecb476c1cc7b4b2d88#file-viafbot-infobox-book-L418), I find a comment describing the states I was looking for between the localClaims (scraped from various Wikipedias) and the remoteClaims (already existing in Wikidata). I wrote:

    """there are three states:
    noMatchingClaim, so we add our claim
    matchingClaimUnsourced, so we add our source
    matchingClaimSourced, claim was already present and had the same source, do nothing"""

Then I proceed to try and find these states by writing what is a basically a big decision tree. So big that it's a text-wrap nightmare, 8 blocks deep.  


    noMatchingClaim = False
    matchingClaimUnsourced = False
    matchingClaimSourced = False

    for remoteClaimList in remoteClaims.itervalues():
        for remoteClaim in remoteClaimList:
            if localClaim.id == remoteClaim.id:
                if localClaim.getTarget() == remoteClaim.getTarget():
                    #now we see if a our source is there
                    for remoteSourceDict in remoteClaim.getSources():
                        for remoteSourceList in remoteSourceDict.itervalues():
                            for remoteSource in remoteSourceList:
                                if remoteSource.id == localSource.id:
                                    if remoteSource.getTarget() == localSource.getTarget():
                                        matchingClaimSourced = True
                    if not matchingClaimSourced:
                        matchingClaimUnsourced = remoteClaim

Very unfortunately I missed about what to do if we have a *matching claim with a conflicting value*, it should be have been recorded as noMatchingClaim, but I overlooked it because of the heavily nested structure. To fix this I think flat, and functional would have been better. And of course, some testing wouldn't have gone amiss either.

Trying to be more, not confusing.

 
