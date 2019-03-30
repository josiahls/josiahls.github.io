---
layout: post
title: Creating an 8 Queen Solver in C++ Part 2
description: Making an 8-Queen Solver in C++
---

I have finished the 8 Queen Solver. Programming in C++ was interesting. I learned that unless I have already built 
frameworks in C++, it is not a good idea to try to build one with so little experience. I think that this is part of 
"trying to be too smart".

## Version 1-3
I started attempting to add polymorphism immediately. For example, I would have an AbstractNode class that then would have a 
Node class derived from the Abstract class. The main issue was not understanding the issue of pointers and adding 
them to a vector. I was attempting to do:

```c
vector<Node> children;
```

I wanted the Node to then be added to this vector. The Node should be templated so that the value of each node could be different. 
The utility of this was obscure however, and I think that I was just wanting to do it in an exercise for handling 
polymorphic class's pointers. I am primarily motivated to do this due to having another project on a neural net that 
I want done in C++. It is possible that I need to use different types of pointers.

I think that it might be important to do a test bench project instead of experimenting in the actual class. 
I believe this to be the case since otherwise I have difficulty handling large errors that come form experimenting on a large program. 

Another reason why this project was so painful to implement in OOP and polymorphic programming might have been the 
desire to design a project but not adequately test the design I was trying to do. I would often make a small change, 
then get 20 different errors from other parts of the code. This made the error fixing long and frustrating. And I have 
done this before with AI, and testing only parts of it. 

## Version 4 (final)
So this is what the final project looked like. I did not use the exceptions class either. The end result is a 
program that can execute an 8 queen program and solve it in 10 seconds average. There is no polymorphism in this final project. I hope to attempt a polymorphic system again however. I need to understand the different pointers and possibly look into higher level concepts such as policies, friends, and others. 

![Project Structure]({{ site.url | absolute_path}}/assets/images/2018-2-13-eight-queen-solver-pt2-img1.png)

I will definitely be making a test bench for this. The other thing I want to add is unit testing. I tried getting the 
gtests working on the project however it seemed to demand more manual operations to get it working. 

So An interesting issue I had here was not being able to directly access the elements in the 
priority queue. So I made a second one as a set to determine if an element was in the queue.
The main issue I had here was that I tried extending the priority queue class so I only had one 
class. I may try this on a future project because this is kind of ridiculous to have 2 array style
variables that have the same elements just in different orders.

I took this code from a previous project I made in Python. At this point I would have been 
filtering out elements that had different path_cost + h, however since this is just hill-climbing,
there is not an immediate requirement to do this. 

## Conclusion
I still plan to program in C++, however compared to Python, this was hellish. Maybe this had to do with me trying to "Javafy" my C++ program. Polymorphic programming in C++ is another beast to learn. I'm motivated mostly because the people at Google made freaking TensorFlow in C++, why can't I? 

