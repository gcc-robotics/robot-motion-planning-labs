---
layout: post
title: "Lab 0: Setting Up"
description: If you need to configure your computer for use with these labs start here!
---

If you are using GCC Robotics Lab computers you can skip this lab and head 
straight over to Lab 1. This guide will be useful if you want to configure your 
personal laptop so you can continue working at home.

To be able to follow along with this series of labs you will need to have 
several prerequisites installed and configured on your computer. This lab will 
guide you through the process of getting all of the installed and configured 
correctly.

### Prerequisites

* Ubuntu 14.04
* ROS Indigo
* iRobot Create and Microsoft Kinect Drivers

Additionally to connect to the iRobot your computer needs to have Bluetooth. If
your computer does not have Bluetooth you can buy a USB adapter or use the Lab 
computers.

Let's jump right in and start with Ubuntu.

### Setting Up Ubuntu

This series of labs was written specifically for Ubuntu 14.04 so you need to 
make sure that this is the version you are installing.

* [Download the Ubuntu 14.04 Desktop ISO][ubuntu-desktop-download]
* [Burn the downloaded ISO file to a DVD][ubuntu-dvd-burn-guide]
* [Follow the Ubuntu install guide][ubuntu-install-guide]

### Setting up ROS

Again this series of labs was written specifically for ROS Indigo Igloo so you 
need to make sure that this is the version you install.

Boot and login into your newly installed Ubuntu 14.04 Machine.

Next make sure that your computer has internet access we will install the rest 
of the requirements over the internet.

We will install ROS from the __Terminal__. The __Terminal__ is a text based 
input / output program which allows you to run different commands. You will 
learn more about the terminal in Lab 1.

Open the Terminal by Pressing `Ctrl` + `Alt` + `T`

![Small Empty Ubuntu Terminal Window][small-empty-terminal]

Type the following command into the new terminal window and hit enter:

	sudo apt-get update && sudo apt-get upgrade -y

You will be asked for your password if you specified one during the Ubuntu 
installation. The command may take quite a long time to complete. That is ok.

Now we are ready to start installing ROS Indigo, run the following commands in 
sequence in the same terminal window.

1. 

		sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
		
2.
	
	sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
	
3.
	
	sudo apt-get update
	
4.
	
	sudo apt-get install ros-indigo-desktop-full
	
5.
	
	sudo rosdep init
	
6.
	
	rosdep update
	
7.
	
	echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
	
8.
	
	source ~/.bashrc
	

Done! You have successfully installed ROS on your system.

__Before continuing with the installation you should restart your computer to 
make sure everything went well.__

If you have any problems during the installation consult the 
[ROS Indigo install guide][ros-indigo-install-guide].

### Installing iRobot Create Drivers

Next we need to install the iRobot create drivers which will allow us to control
the robot over Bluetooth using our Ubuntu computer and ROS.

### Installing Microsoft Kinect Drivers

The last thing we need to is to install the drivers for the Microsoft Kinect 
camera which we will be using to track colored objects.

Open a new Terminal (or use an existing one if you still have it open) and run 
the following command:

* 
	
	sudo apt-get install libfreenect-dev ros-indigo-freenect-launch


Done! You're ready to move on the Lab 1!

[ubuntu-desktop-download]: http://www.ubuntu.com/download/desktop
[ubuntu-dvd-burn-guide]: https://help.ubuntu.com/community/BurningIsoHowto
[ubuntu-install-guide]: http://www.ubuntu.com/download/desktop/install-ubuntu-desktop
[ros-indigo-install-guide]: http://wiki.ros.org/indigo/Installation/Ubuntu

[small-empty-terminal]: ../images/post/small-empty-terminal.png
