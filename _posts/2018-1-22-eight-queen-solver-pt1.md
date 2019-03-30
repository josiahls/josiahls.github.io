---
layout: post
title: Creating an 8 Queen Solver in C++ Part 1
description: Making an 8-Queen Solver in C++
---

This spring 2018 semester I am studying AI under Dr. Jugan in his ITCS 3153 course called Intro to 
Artificial Intelligence. The first assignment we are doing is solving an 8 Queen problem that involves intelligently 
placing 8 Queens in a chess board so that none have paths that intersect with others. I have decided to build this 
in C++ because I want to farther understand C++ and how to build solid applications using it.

![Code Snippet 1]({{ site.url | absolute_path}}/assets/images/2018-1-22-eight-queen-solver-pt1-img1.png)

The current state of the project as of today was jumping into creating the overall framework. 
I needed a Node class, a Problem class, and eventually a Search class.

The code as you see above is simply testing the Node creation, the calling of overridden methods, 
and showing the state space.

![Code Snippet 2]({{ site.url | absolute_path}}/assets/images/2018-1-22-eight-queen-solver-pt1-img2.png)

Above is an example of the Node class. One of the difficulties I had was getting the expand method to not crash 
the program immediately. I spent a good part of 40 minutes getting the toString to even work and 
I will describe why later down.

![Code Snippet 3]({{ site.url | absolute_path}}/assets/images/2018-1-22-eight-queen-solver-pt1-img3.png)

Most of my time was spent trying to get the AbstractNode class to work without crashing the program. 
This was due to me insisting on using virtual methods since I wanted legitimate class inheritance against the 
better judgement of some good people on stack overflow.

One of the issues was accidentally attempting to initialize the AbstractNode class. Obviously the point of 
abstract classes is to not initialize them, but initialize their derived classes instead. However, 
I need the virtual methods in the AbstractNode to return nodes, and since the AbstractNode class does not have 
knowledge of the types of nodes that need to be returned, I need to somehow have the virtual methods returning 
an AbstractNode.

This is resolved by both expecting the methods to return a vector of AbstractNode's and return wrapped references 
to AbstractNode's. This allows me to override the methods and initialize them in the derived classes such as the Node class.

However I am still learning how the virtual methods work, and will need to refactor the parameters to be references, 
and constants. In my neural networking project, one of the issues I am having is having virtual methods that are 
templates. Since the entire class is a template as opposed to the methods being templates I am able to use these 
generics. Unfortunately, if I decided to do what I want to do in my neural networking project, then I need to 
rethink how to have a parent class that involves generics but is not in itself a template class.

One of the major issues was having the methods made "pure virtual". Now, when I remove the "= 0" I get this error: 

Now the important part of this error is the statement: "undefined reference to". This confused me a lot because 
the method to me is defined. However, it is possible that the actual body is part of the definition. 
I think that the issue is that you can define the methods in the headers without a body, and so when switching to 
inheritance, it can be difficult to switch gears and realize that the methods need to be defined with bodies, 
even if they are just set to zero.

One of the major concerns moving forward is the build up of nodes that have not been destroyed. 
I am worried when the program actually tries to solve the queen problem, there will be large memory errors 
since instances are not be destroyed properly. But we will see. Hopefully once I pick this up again this weekend, 
I can refactor the code and improve it. Luckily I started early and already understand 95% of what I need to have made.