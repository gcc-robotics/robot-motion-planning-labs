---
layout: post
title: "Lab 1: Getting Started!"
description: "This lab will introduce you to the linux operating system, Terminal, 
Terminal commands, iRobot driver, and Teleop keyboard controls of iRobot."
zipFile: gh-pages.zip
---

This lab is designed to serve as a jump start into Linux and ROS. By the end of 
this lab you should be able to control your iRobot Create base with a teleoperated keyboard.


This lab was written for Linux and tested under Ubuntu 14.04 LTS.

Introduction to Linux
--------------

Linux is open source operating system and is developed by the community. There are 
many different version of linux available, and Ubuntu is one of these operating 
systems that is most commonly used. Hence, we will be using Ubuntu; more precisely, 
we will be using Ubuntu 14.04 LTS. For more information about the linux operating 
system, there is a course at Glendale Community College (CS/IS 172) available.

Introduction to Robot Operating System (ROS)
-----------------

#### subtitle?

The Robot Operating System (ROS) is a flexible framework for writing robot software. 
It is a collection of tools, libraries, and conventions that aim to simplify the 
task of creating complex and robust robot behavior across a wide variety of robotic 
platforms. Why? Because creating truly robust, general-purpose robot software is hard. 
From the robot's perspective, problems that seem trivial to humans often vary wildly 
between instances of tasks and environments. Dealing with these variations is so 
hard that no single individual, laboratory, or institution can hope to do it on their own.

How to Boot into Ubuntu
--------------
The computers in this lab are equipped with both Windows and Ubuntu operating systems. 
In order to boot into Ubuntu Linux, restart the computer to see the grub menu 
(a magenta colored page). Windows is the default, so you will need to make a selection 
for Ubuntu, and voila! Now you are booted into ubuntu.

Command Line
--------------

ROS uses the command-line in order to accomplish many of its tasks. Let's begin 
by connecting to our robot:

* Log in to the computer. Include relevant information (password, etc) here

* Open a Terminal window via the Applications ... Accessories ... Terminal menu 
options (or the crtl + alt + t shortcut)
	* Try opening a new Terminal tab using Control-Shift-T. (Remember this shortcut 
	- you'll be running lots of processes later, one in each tab.)

* Be sure your robot is on and has an "Element Direct" bluetooth receiver attached 
at its 25-pin serial connector in the center. Make a note of the four hexadecimal 
digits on the bluetooth receiver -- since there will be several on in the room, 
you'll need to be sure to pair with the appropriate one.

* Open a new tab by right-clicking or the control-shift-t shortcut
	* Each new tab or Terminal window will hold a separate process -- be ready to 
	open lots of new tabs!
	* A process is code that your computer is continuously executing - These specific 
	processes you will be running keep running until you stop them. You know something 
	is a process because the Terminal window will not prompt you for more input.

* Before we connect to the bluetooth receiver, we want to remove any old devices 
that may have been previously connected. Open a new tab and type or copy/paste the 
following command: 

			$ sudo rm /dev/rfcomm0

		It will prompt you for the lab password, since this is a system file.
__Note__: Though the cursor will not move, the password will be typing. This is 
Terminal's security feature to protect the password.
It's likely that it will reply "No such file or directory ..." this is completely 
OK, it simply means no previous bluetooth connections were established.

* Search for bluetooth devices in the area by typing the following command: 

			$ hcitool scan

Find the Element Serial device with your final four hex digits.
Next, run the command 

		$ sudo rfcomm connect 0 ADDRESS 1

	* Where ADDRESS is the full hex address of your device, e.g.,

				$ sudo rfcomm connect 0 00:0A:3A:2E:CB:3E 1

	* Note: Terminal uses control-shift-c for copy and control-shift-v for paste; 
	all other programs don't include the shift. It might take some getting used to!
If you connect successfully, Terminal will reply with Press CTRL-C for hangup


Terminal Commands
--------------

Before moving on, you need to learn how to use some of the Terminal commands. 
We will only go over few and essential commands.

* __pwd__: This command (print working directory) allows the user to know which 
directory you are currently located: 

		$ pwd

* __ls__: This command (list) get the list of the available diretries in your 
current directory:

		$ ls

* __cd__: This command (change directory) get the list of the available diretries 
in your current directory:

	* To navigate into the root directory

			$ cd /

	* To navigate into the home directory

			$ cd ~

	* To navigate up one directory level

			$ cd ..

	* To navigate to previous directory

			$ cd -

	* To navigate to multiple levels of directory

			$ cd /directory/subdirectory/subsubdirectory
		
* To open source files to editor, you will have two possiblities.

	* __gedit__: Built in editor:

			$ gedit source.cpp

	* __subl__: Sublime text editor, installed on the lab computers, but private 
	editor:

			$ subl source.cpp


Launching the iRobot Create Driver
--------------

In order to command and drive the iRobot Create base we need to run a driver. 
A driver converts high level commands into voltages that control the hardware. 

* Open a new tab by right-clicking or the control-shift-t shortcut, and type the 
following:

			$ roscore

* Again, open a new tab by right-clicking or the control-shift-t shortcut

* We first want to set up our environment variables, we essentially want the 
TURTLEBOT_SERIAL_PORT variable to connect at “/dev/rfcomm0”
	* Type or copy paste the following two commands:

				$ echo "export TURTLEBOT_SERIAL_PORT=/dev/rfcomm0" >> ~/turtlebot/devel/setup.sh

				$ source ~/turtlebot/devel/setup.bash

* Now we run the launch file using roslaunch. roslaunch is a tool that starts multiple 
nodes. Type or copy paste the following command:

				$ roslaunch turtlebot_bringup minimal.launch

	* This will beep when connected


Teleop Keyboard
-----------

* Open a new tab by right-clicking or the control-shift-t shortcut, and launch 
the teleop keyboard node by typing or copying and pasting the following:

			$ roslaunch turtlebot_teleop keyboard_teleop.launch

* You should see the following menu:
This is an awesome lab!
			Control Your Turtlebot!

			Moving around:

			 u    i    o

			 j    k    l

			 m    ,    .


			q/z : increase/decrease max speeds by 10%

			w/x : increase/decrease only linear speed by 10%

			e/c : increase/decrease only angular speed by 10%

			space key, k : force stop

			anything else : stop smoothly


			CTRL-C to quit

* Get moving! You are now ready to control your robot with the above keys. Try 
moving in certain shapes, i.e., squares, triangles, etc.

Creating a Workspace
-----------------

A catkin workspace is a folder where you modify, build, and install catkin packages. You 
will using catkin workspace for all of the labs. 
	

* Follow these instructions to create a ROS workspace.

		$ mkdir -p ~/name_your_ws/src
		$ cd ~/name_your_ws/src
		$ catkin_init_workspace

* Now your workspace is ready. The root of your workspace is ~/name_your_ws/ 
	  and ~/name_your_ws/src is your source space. The source space is where you will store 
	  your labs. These are called nodes and will be covered in Lab 2.

Catkin_make
-----------------

The catkin_make command is a tool for building code in a catkin workspace. This is
similar to compiling in C++.

  * First and foremost, you must call "catkin_make" command in root of your catkin workspace.
    Assuming your catkin workspace is in ~/root.

		$ cd ~/root
		$ catkin_make

  * A catkin workspace is a place where you modify, build, and install catkin packages.

  * At first catkin workspace should contain /src directory.

  * The /src directory is the directory which contains the node (next section will cover)
  , which is where your codes will be stored and modified.

  * As a result of catkin_make command should have created /devel and /build folders in your root.