Title: Synthetic Training Data For Rare Object Detection in Computer Vision
Date: 2017-08-05 03:13
Author: max
Category: research-notes
Slug: llnl17
Status: published

My internship this summer at Lawrence Livermore National Lab was nothing if not practical. The exceedingly real objectives of government science gave my first foray into deep learning gravitas and purpose.

The domain was satellite imagery, and the research question was whether computer vision could be trained to identify objects for which we have no training data. This presents a problem for the family of convolutional neural network algorithms (CNNs) which on the contrary require lots examples to learn from. The idea that I implemented to address this conundrum was to "synthetically" manufacture training data with renders from CAD software, and then test its performance on "natural" (i.e. real) examples. To experiment we used the C5 airplane -- one of the largest in existence, measuring about 80 pixels at Google Earth maximum zoom -- and found that even in its simplest form, the problem is quite hard. The naïve approach of just slapping an overhead snap from sketchup onto a background yielded almost no benefit above guessing. With randomization in the brightness, contrast, position, and emulation of lens impurities, in the synthetic training images, the best performance we managed to eke was a beginning-to-be-promising 78%.

Of course the details of the neural net were important as well as novel-portion of  optimizing the synthetic image pipeline. The base CNN which I started with was a standard ["VGG" implementation](https://arxiv.org/pdf/1409.1556.pdf), using [Keras](https://keras.io). Desirous to get beyond off-the-shelf, I found that: early stopping, extra dropout between the convolutional layers, added gaussian noise at the input layer, and label-persevering transformations all helped with the cause. Learning about and wielding these techniques in practice felt very powerful, and I can understand why the buzz about them exists. I am very glad to have added deep learning and neural networks to my tool belt. In fact it has inspired me to go back to [previous projects](http://notconfusing.com/machine-learning-in-3rd-grade/) and see how the method can improve upon the classic algorithms.

Another summer leveling up without confusion.

[![]({static}/images/uploads/2017/08/Selection_050.png){.size-large .wp-image-4137 style="width:474px !important"}](http://notconfusing.com/images/Synth-Train-Poster_v3.pdf) Poster (click for pdf).
