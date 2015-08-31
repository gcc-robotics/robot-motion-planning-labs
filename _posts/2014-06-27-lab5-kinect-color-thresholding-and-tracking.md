---
layout: post
title: "Lab 5: Color Thresholding and Tracking using the Kinect"
description: "This lab will guide you to create a program that analyzes images, one-at-a-time, from the Kinect's video stream and openCV."
zipFile: gh-pages.zip
---

Introduction
--------------

Computer vision is a rich source of input and one of the more computaionally challenging, because the things we might like to know about the environment (where a particular object is located, where there is freespace available to navigate) is wrapped up in very intricate ways among the pixels of an image. 


Preliminaries
--------------

starter code and setting up the kinect camera

check to see if connected and seeing images on topic


Introduction to Thresholding
--------------

It is advantageous to differentiate uniform regions of uniform color, e.g. colored objects, etc..
In this lab exercise you will use the hue-saturation-value color space. it is a transformation of red-green-blue (RGB) color space that tries to group perceptually similar colors in the same part of the space. 

The hue axis, which is circular, intends to represent roughly what we mean when we use different color names: green, cyan, yellow, etc. The value axis represents the amount of light present in a pixel -- that is, it's greyscale intensity, independent of hue. Finally, the saturation axis intends to capture roughly what we mean by the "richness" of a color, e.g., a deep scarlet would have a high saturation; a pale pink would have a low saturation. By using HSV (hue-saturation-value) and RGB (red-green-blue) thresholds for a particular color, it should be possible to extract regions reliably. 

*include picture here*

Getting Started
---------------
This lab will guide you to create a program that analyzes images, one-at-a-time, from the Kinect's video stream.

In order to process pixels from the Kinect, you will use the OpenCV library. Like ROS, OpenCV is maintained by Willow Garage and is by far the most popular (and some might argue most powerful) computer vision library available today. In addition, you will take advantage of the OpenCV interface to add keyboard-based remote-control capabilities to your robot. Next week, you will use vision and robot control together to implement an autonomous point-to-point navigation routine.

OpenCV Windows
--------------

In order to let you see what the Kinect is seeing, we create windows through OpenCV.
This happens in the initialization functions:
cv.NamedWindow('image')
if you haven't run the program yet, go ahead and run it (Instructions are in the Getting Started section!).

###Window Positioning###

You might have noticed that the when the windows appear, they overlap each other quite a bit. This is because we have the ability to tell the windows where they should first be placed. We do this through this code:
cv.MoveWindow('threshold', 10, 0)
Where we have moved the top left corner of the window to be at the point on the screen: (0, 10)
OpenCV as well as a lot of other computer programs use a different coordinate scheme than normal math does. This means that the point (0,0) is at the top left corner of a window, and the numbers count by pixel. So the point (0, 10) is 0 pixels over from the left edge of the screen and 10 pixels down from the top edge of the screen.
Here is a diagram of how it works: 

*insert picture here*

### Sliders ###
While two of these windows simply have images in them, one of them contains a bunch of sliders. Most of the code to make the sliders work are in OpenCV and we don't have to worry about them.
However, we are responsible for actually telling OpenCV that we want sliders.
We do this like so:

The first argument is the name, the second is the window we want to put it in, the third is the default value, and the fourth is the max the slider should go to.
The last is a function, a callback (we'll explore these in more detail below!), that happens when someone moves the slider to a different value.

Callback Functions
--------------

Callback functions are functions that are called when an event occurred. Events are usually defined as some type of input. In this lab we will set up callback functions for mouse clicks, keyboard presses, and data reception from the Kinect.
The callback functions we'll look at today are triggered every time one of these events happen, which means that the functions must cover all the possibilities we think we'll need. 

Image Processing with OpenCV
-------------

### Drawing on Top of an Image ###

OpenCV also allows users to manipulate images by drawing shapes on them. We will be completing the blob finding part of the program by creating a box around the largest contour area found by thresholding, and a circle at its center.

This occurs in the function find_biggest_region.
This function's first four lines uses the OpenCV library to find all of the closed contours of self.threshed_image
The check if len(contours)>0: simply asks if there were any contours at all
Then, the code finds the largest contour by area
At the moment, it draws a red box using cv.PolyLine at the vertices (42,42),(42,100),(100,100),(100,42) and a yellow circle at (42,42) with cv.Circle
Remember that the coordinate system has (0, 0) at the top left corner of the image!
Change the code so that it draws the bounding box around the largest found foreground region and draws the circle at the center of that bounding box.
Note that you already have the data you need (it's in br, short for "bounding rectangle"), but you'll want to examine that (by printing it out as it changes) in order to extract the information needed to add the drawing. The bounding rectangle br is a list with four components:
the upper-left vertex's x-coordinate
the upper-left vertex's y-coordinate
the width of the rectangle, and
the height of the rectangle.
