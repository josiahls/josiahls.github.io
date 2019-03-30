---
layout: post
title: Neural Networking in C++ Woes :(
description: First Attempt Trying to Build a Neural Net from Scratch
---

Over the past month I have been attempting to create my own neural net framework in C++. 
There were many great tutorials that I worked through during the last semester that gave me the confidence to 
attempt something like this. Neural Networks in C++ was an extremely helpful tutorial that got my feet wet. 
I think that Dave covered enough to help jump start, but left out enough to force the viewer to start creating on their own.

There was a series Sentdex had that worked through some important concepts in both machine learning and neural networking. 
Obviously neither of these worked as a step by step "how to make the next Alpha Go AI" tutorial, however that was not the point. 
Sentdex showed me concepts such as KNN and SVMs which are extremely useful for general machine learning. He also went through 
Tensorflow, which is an extremely easy Neural Networking framework.

For me, the frustrating thing about Tensorflow was the positive of it. You do not need to understand neural networks 
to make a decent neural network. This made it difficult to both troubleshoot and truly attempt to make something unique. 
This is why I decided to create a NN in C++ both because C++ is pretty explicit about what is happening and I need to understand C++ anyways.

Making a NN in C++ most likely is not actually that hard. I spent a long time figuring out how to handle polymorphism 
in C++ which can be sort of (extremely) frustrating.

The issue I am having is trying to use an abstract class to represent multiple classes. This allows me to only have 
one addLayer() method in the Net class. However, since all layers should be able to have their outputs pre-set, 
I should be able to have the abstract class define a method for this called setOutput(T inputs). The problem is that 
I need the inputs to be generic. If the layer I am trying to set the outputs to is 2 dimensional layer then the inputs 
will need to be 2 dimensional, but if they are 1 dimensional you get my point. The issue is that virtual methods, 
at the least the way I am attempting implement them, cannot have generics due to reasons involving a vtable. 

![Neural net Architecture]({{ site.url | absolute_path}}/assets/images/2018-1-18-neural-net-woes.png)

However I have seen code that works the way I am wanting. The issue is if I add generics to the ILayer class, 
I end up having to up-end the Layer class and any child classes and usually I get convoluted errors. 
Unfortunately, since I am new-ish to C++ I am not super amazing at working with the templating system and not knowing 
what I can and cannot do. The Github is noted here: JImageNet.

What I am worried about is having to scrap large portions of the Layer code to make it easier to follow because right now, 
making a 1 minute change causes 30 minutes of bugs.

