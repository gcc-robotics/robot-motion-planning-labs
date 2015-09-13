---
layout: post
title: "Lab 6: Robot Tracking and Navigation Using Color Thresholding"
description: "In this lab, we will be enabling your robot to move to any position in the Kinect's view. We'll select a point by clicking on the screen and use visual servoing to arrive at that point."
zipFile: gh-pages.zip
---

Introduction
--------------

This lab will serve as a classic example of a subfield of robotics known as servoing, in particular, vision-based servoing. The term "servoing" refers to controlling a system by continually measuring the error between the system's current state and its desired state -- and then taking action to reduce that error. Visual servoing uses an error defined in an image, rather than in the physical spatial environment of the robot. 


Preliminaries
--------------

We have provided starter code to begin with. As usual with any starter code please take the time
to understand what is going on. This code combines the control you had over your robot
in labs 1, 2, 3, and 4 with the use of the Kinect in Lab 5.

Dressing Up Your Robot 
--------------

Now, to combine the color tracking that you have done previous with this lab, you should select a colored felt piece to place on your robot. First, make sure that you can get the thresholds for this felt piece right, this will enable you to track your robot as it goes across the screen.

Drive your robot around manually, and make sure that the thresholds still work while it's visible by the Kinect! 

Getting Started 
-----------------

Although you all are likely to come up with different ideas on how to get your robot from Point A to Point B, one idea that will come in very useful is that of Finite State Machines. In fact, we request that you code the movement of your robot within a Finite State Machine. 

Next try changing this finite-state machine in a couple of ways. First, change the finite state machine so that it


* prints the difference in the robot's (x,y) image position between its initial location when it starts in "Forward" state to its position when it transitions into "Backward" state.


* remembers the robot's old image position. This will require defining one or more variables, depending on whether you have a separate name for the x and y components or a single variable for the list/tuple of both components


Why bother? These changes are useful one for computing the robot's heading in the image, i.e., move for two seconds and compare the pre- and post-locations. 


Getting and displaying a right mouse-click
--------------
In order to move your robot within the Kinect's view we'll need to capture the x and y coordinates from your mouse-click. OpenCV provides a callback funcion to set the mouse handler for a specified window. This has been done in the starter code. Your next step is to draw a circle on the clicked point using OpenCV's draw functions so that you can see exactly where your robot should navigate to.

Getting from Point A to Point B 
--------------
Now that you have the robot's heading, let's get moving! We can break this up into intermediate steps. 

* Consider comparing your current heading value with the desired heading value. (The desired heading value should be computed the same way, but with your clicked point)

* Next consider the case when the robot is on the left, facing rightward, and wants to get to a target on the right of the image. 

* Once you have the right-direction version working, then try adding the left-direction version as a special case.



Other hints and suggestions... 
--------------

