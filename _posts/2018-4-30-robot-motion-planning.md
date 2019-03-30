---
layout: post
title: Robot Motion Planning via Visibility Graphs
description: Using OpenGL and Python for Simulating Robot Navigation
---

I have some images below of what I have been doing for my ITCS 6152 master's robotics motion planning course. 
Recently I competed in a IEEE robotics competition. I needed to create a system that could allow simulated sensor 
readings so that the robot could know where it is in a map that is 3 dimensional. The motion planning was going to 
only need to be 2 dimensional since the robot is unable to travel along the z axis on its own.

I used Python, OpenGL, and PyGame to create a 3D simulation of the robot moving through space and colliding with obstacles. 
Below shows an image of the robot and the path it is taking (from bottom to top). However, this is actually a robot 
traveling through 3D space. The grey cube is the robot. A* search can be executed on it, and it is able to travel while 
'gravity' and wall collision is being simulated. Unfortunately, I am still working on the visibility graph. 
I implemented A* search on the map to get the robot from its current state, to a goal state. 
The A* as of now is extremely slow.

| ![2018-4-30-robot-motion-planning-img1.png]({{ site.url | absolute_path}}/assets/images/2018-4-30-robot-motion-planning-img1.png) |
|:--:|
| *Fig 1: The grey cube is the robot. It started from the bottom left corner and is traveling to the upper right corner.* |

| ![2018-4-30-robot-motion-planning-img2.png]({{ site.url | absolute_path}}/assets/images/2018-4-30-robot-motion-planning-img2.png) |
|:--:|
| *Fig 2: This a 3 dimensional view of the robot. The path markers hover above the 3 dimensional surface.* | 

The grey cube is the robot traveling from a start location to a goal location. The red plane above is a 2D 
representation that is being layered over the top. Below you can see that the 2D representation has grown the obstacle 
sizes. This allows for easier motion planning.

| ![2018-4-30-robot-motion-planning-img3.png]({{ site.url | absolute_path}}/assets/images/2018-4-30-robot-motion-planning-img3.png) |
|:--:|
| *Fig 3: Here is a 2 dimensional overlay for motion planning. This also shows the beginnings of a visibility graph* |

Below is an example of the 3D course converted to the 2D representation with grid lines layered over top of it. 
These grid cells are what the A* search algorithm uses to find suitable paths for the robot.

| ![2018-4-30-robot-motion-planning-img4.png]({{ site.url | absolute_path}}/assets/images/2018-4-30-robot-motion-planning-img4.png) |
|:--:|
| *Fig 4: This is a discretized view of the course divided up as a grid of 1x1 centimeter cells. The obstacles are dilated by the robot's width and height to prevent the robot from running into the obstacles* |

Overall this project did not go the way I wanted. Since I anticipated having a physical robot, a large portion of the 
visuals needed to be built quickly. I did not have time improve the searching speed. Ending system seems to work most 
of the time, however I found that converting my 3D collision detection to 2D does not work well. It seems that there 
is still a large amount of bug testing needed.





