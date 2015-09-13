---
layout: post
title: "Lab 4: Advanced Sensing"
description: "Using reactive control to follow lines on the ground"
zipFile: gh-pages.zip
---


Introduction
--------------

Finite State Machines (FSM for short) were introduced to you in the previous lab. In this 
lab, you will be using FSM in order to to complete more complicated tasks using more advanced 
sensors on the iRobot.

Preliminaries
--------------

This lab will require you to make use of FSM again in order to program the iRobot to follow colored 
lines on the ground. Use the instructions from the Getting Started lab in order to 
connect to the create base and launch the drivers. Do not launch the keyboard driver. 

Sensing
--------------

Similar to the last lab, we will be observing sensor data. The last lab made use of the 
bumper sensors on the iRobot. In this lab, we will be using the more advanced cliff sensors.
The cliff sensors are located beneath the iRobot:

![iRobot Bottom View][irobot-bottom-view]

The iRobot has a total of four Cliff sensors, two near the front center of the robot and two 
more near the sides of the robot. To make this lab easier we will only be using the center two 
sensors. Of course nothing is preventing you from using all four to complete the tasks in this 
lab if you wish.

These sensors detect the reflectivity of the surface beneath them which allows us to use them to
detect when the robot drives over a black line on white ground or a white line on black ground. 
In cases where the ground is the right shade of grey (Like our lab!) we can detect both black and
white lines.

Examining the Sensor Data
--------------

To start off we need to understand what kind of data the Cliff sensors provide. The return Integer
values between 0 and 1400 with lower values representing less reflective surfaces (Black) and higher
values representing more reflective surfaces (White). 

Here are some sample readings from the iRobot Cliff sensors:

![iRobot Bottom View][irobot-cliff-sensor-graphs]

The top two graphs represent the two front center Cliff sensors with one being offset slightly to the 
left the other to the right. The "Far" Cliff sensors are the ones near the sides of the robot.

The graphs represent the data from the Cliff sensors over a four seconds period while driving over 
white and black lines on the gray ground of the lab. An upward spike in the graph represents the robot
driving over a white line (More reflective, higher sensor values) and a downward plunge in the graph 
represents the robot driving over a black line (Less reflective, lower sensor values).

Notice that while all the graphs have the same range of 0 to 1400 they all have different values for 
the same piece of ground. This is an inferent discrepency between the individual Cliff sensors on the 
iRobot. The Cliff sensor values for the same piece of ground will also be different for two different 
iRobots so it's a good idea to try and use the same one for the duration of this lab. You will have to 
account for these discrepencies in your code.

Viewing Live Cliff Sensor Data
--------------

The ROS driver for the iRobot Create publishes a stream of sensor data whenever 
it is connected to the robot. To start, we'll use ROS's command-line tools in order 
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
[irobot-cliff-sensor-graphs]: ../images/post/ir-reading-sample.png
[line-follower-turn]: ../images/post/line-follower-turn.jpg
[line-follower-foward]: ../images/post/line-follower-foward.jpg
