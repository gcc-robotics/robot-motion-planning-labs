---
layout: post
title: "Lab 3: Finite State Machines and Sensing"
description: "This lab will cover Finite State Machines to manipulate the robot 
using the bumper sensors on the iRobot."
zipFile: gh-pages.zip
---

Introduction
--------------

FSM or simply state machine is a model to design computer programs. Most of robots
use FSM to complete certain tasks. In this lab, you will be using the iRobot's 
bumper sensors to define certain actions when the bumper sensors are triggered.


Preliminaries
--------------

This lab will involving FSM (Finite State Machines) to control the iRobot to carry
out certain tasks. Use the instructions from the Getting Started lab in order to 
connect to the create base and launch the drivers except the keyboard driver. 

Finite State Machine
--------------

State machines are used in robot system; it is part of their overall strategy for 
accomplishing tasks. Usually, each state corresponds to a well-defined subtask, 
and the robot transitions from state to state depending on the input data 
sensors, etc…).

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

	* Try echoing the sensor messages and gently tap the bumpers of your iRobot.
	  This should trigger different sensor messages on your Terminal.

Returning to FSM
--------------

The example code includes few functions that make up the FSM itself. These functions
should include:
	
	* state_start

	* state_forward

	* state_backward

	* state_bumper_triggered

Read over the functions and determine the relationship among the states. The transition
between the states are triggered by external events, such as elapsed time or a sensor
trigger.


In this lab, you will be adding multiple states in order to carry out the task of
following the walls of this classroom. This task must be done through use of FSM.
The skeleton of the codes are provided in the Zip folders.

