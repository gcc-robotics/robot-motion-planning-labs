---
layout: post
title: "Lab 4: Advanced Sensing"
description: "Using reactive control to follow lines on the ground"
zipFile: gh-pages.zip
---


Introduction
--------------

Jezmin will write this!!!

Preliminaries
--------------

This lab will involving FSM to control the iRobot to follow guided lines. 
Use the instructions from the Getting Started lab in order to 
connect to the create base and launch the drivers except the keyboard driver. 
This lab will also be using FSM like the previous lab.

Sensing
--------------

Similar to the last lab, we will be observing sensor data. Last lab dealt with 
bumper sensor; however, in this lab, we will be using cliff sensors. The cliff 
sensors are located beneath the iRobot. These cliff sensors are emitters and 
detectors of infrared light. The iRobot has four of these cliff sensors, 
one front-left, one front-right, one on the far left and one on the far right. 
For line following, only the front two are needed, though more robust solutions 
might use all four.

Examining the Sensor Messages
--------------

The ROS driver for the iRobot Create is publishing a stream of sensor data whenever 
its connected to the robot.To start, we'll use ROS's command-line tools in order 
to see the data stream that ROS is providing. These "data streams" we've been 
using are known as topics in ROS terminology.

	* At your Terminal run rostopic to see all the different ROS provided commands
	  related to topics.

		$ rostopic

	* In particular, run rostopic list to see all the topics available at the momment.
	  Which are the ones you are interested in.

		$ rostopic list

	* If you do not see the topic mobile_base/sensors/core, try reconnecting your
	  iRobot following the lab 1 commands.

	* To print the data flowing through Terminal, we will be using echo command.

		$ rostopic echo mobile_base/sensors/core

	* Try putting different colored item under the cliff sensors and observe the
	  topics printed on your Terminal.

	* The sensors are found under the robot. It is labeled as "Cliff Sensor Openings" on 
	  the picture.

![iRobot Bottom View][irobot-bottom-view]

Sensor Subscribers
--------------

Similar to previous lab, we will be using subscriber once again. However, this 
lab will need to access the data of cliff sensors. Compare the codes to see 
how the subscribers are different for different sensors.

Line-following
--------------

The idea of this lab is:

	* First, place the iRobot so that it's cliff sensors straddle in a line

	* Using FSM, your iRobot will have to follow the line provided

	* When the cliff sensor detects the line, make appropriate state to get back on track

	* The picture will guide you the task a bit more clearly.

![iRobot Foward][line-follower-foward] ![iRobot Turn][line-follower-turn]

To begin, you must be able to find the threshold the colors using the cliff sensor. Use the 
front-left and front-right sensors only. Be careful of the classroom ground color with 
the tapes. To test, start with straight lines and slow curves. Make sure your line-following 
codes are written using FSM.

[irobot-bottom-view]: ../images/post/irobot-bottom-view.jpg
[line-follower-turn]: ../images/post/line-follower-turn.jpg
[line-follower-foward]: ../images/post/line-follower-foward.jpg
