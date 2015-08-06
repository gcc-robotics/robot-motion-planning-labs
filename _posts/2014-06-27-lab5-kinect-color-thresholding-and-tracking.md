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

OpenCV Windows
--------------

Callback Functions
--------------

Image Processing with OpenCV
--------------

Using HSV
--------------