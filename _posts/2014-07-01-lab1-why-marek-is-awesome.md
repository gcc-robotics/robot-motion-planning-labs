---
layout: post
title: "Lab 1: Getting Started!"
description: This is an awesome lab!
zipUrl: https://github.com/gcc-robotics/robot-motion-planning-labs/archive/gh-pages.zip
---

This lab is designed to serve as a jump start into Linux and ROS. By the end of this lab you should be able to control your iRobot Create base with a teleoperated keyboard.


This lab was written for Linux and tested under Ubuntu 14.04 LTS.

Introduction to Linux
--------------
Someone please expand on this.

    Linux = OS (open source)

    Linux mascot = a penguin (Tux)

    Will be using Ubuntu 14.04 LTS

    CS/IS 172 = Linux class (GCC)

Introduction to Robot Operating System (ROS)
-----------------

#### subtitle?

The Robot Operating System (ROS) is a flexible framework for writing robot software. It is a collection of tools, libraries, and conventions that aim to simplify the task of creating complex and robust robot behavior across a wide variety of robotic platforms.
Why? Because creating truly robust, general-purpose robot software is hard. From the robot's perspective, problems that seem trivial to humans often vary wildly between instances of tasks and environments. Dealing with these variations is so hard that no single individual, laboratory, or institution can hope to do it on their own.

How to Boot into Ubuntu
--------------
The computers in this lab are equipped with both Windows and Ubuntu operating systems. In order to boot into Ubuntu Linux, restart the computer to see the grub menu (a magenta colored page). Windows is the default, so you will need to make a selection for Ubuntu, and voila! Now you are booted into ubuntu.

Command Line
--------------

ROS uses the command-line in order to accomplish many of its tasks. Let's begin by connecting to our robot:

* Log in to the computer. Include relevant information (password, etc) here

* Open a Terminal window via the Applications ... Accessories ... Terminal menu options (or the crtl + alt + t shortcut)
  * Try opening a new Terminal tab using Control-Shift-T. (Remember this shortcut - you'll be running lots of processes later, one in each tab.)

* Be sure your robot is on and has an "Element Direct" bluetooth receiver attached at its 25-pin serial connector in the center. Make a note of the four hexadecimal digits on the bluetooth receiver -- since there will be several on in the room, you'll need to be sure to pair with the appropriate one.

* Open a new tab by right-clicking or the control-shift-t shortcut
  * Each new tab or Terminal window will hold a separate process -- be ready to open lots of new tabs!
  * A process is code that your computer is continuously executing - These specific processes you will be running keep running until you stop them. You know something is a process because the Terminal window will not prompt you for more input.

* Before we connect to the bluetooth receiver, we want to remove any old devices that may have been previously connected. Open a new tab and type or copy/paste the following command: 

      $ sudo rm /dev/rfcomm0

    It will prompt you for the lab password, since this is a system file.
__Note__: Though the cursor will not move, the password will be typing. This is Terminal's security feature to protect the password.
It's likely that it will reply "No such file or directory ..." this is completely OK, it simply means no previous bluetooth connections were established.

* Search for bluetooth devices in the area by typing the following command: 

      $ hcitool scan

Find the Element Serial device with your final four hex digits.
Next, run the command 

    $ sudo rfcomm connect 0 ADDRESS 1

  * Where ADDRESS is the full hex address of your device, e.g.,

        $ sudo rfcomm connect 0 00:0A:3A:2E:CB:3E 1

  * Note: Terminal uses control-shift-c for copy and control-shift-v for paste; all other programs don't include the shift. It might take some getting used to!
If you connect successfully, Terminal will reply with Press CTRL-C for hangup





Launching the iRobot Create Driver
--------------

In order to command and drive the iRobot Create base we need to run a driver. A driver converts high level commands into voltages that control the hardware. 

* Open a new tab by right-clicking or the control-shift-t shortcut, and type the following:

      $ roscore

* Again, open a new tab by right-clicking or the control-shift-t shortcut

* We first want to set up our environment variables, we essentially want the TURTLEBOT_SERIAL_PORT variable to connect at “/dev/rfcomm0”
  * Type or copy paste the following two commands:

        $ echo "export TURTLEBOT_SERIAL_PORT=/dev/rfcomm0" >> ~/turtlebot/devel/setup.sh

        $ source ~/turtlebot/devel/setup.bash

* Now we run the launch file using roslaunch. roslaunch is a tool that starts multiple nodes. Type or copy paste the following command:

        $ roslaunch turtlebot_bringup minimal.launch

  * This will beep when connected


Teleop Keyboard
-----------

* Open a new tab by right-clicking or the control-shift-t shortcut, and launch the teleop keyboard node by typing or copying and pasting the following:

      $ roslaunch turtlebot_teleop keyboard_teleop.launch

* You should see the following menu:

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

* Get moving! You are now ready to control your robot with the above keys. Try moving in certain shapes, i.e., squares, triangles, etc.
