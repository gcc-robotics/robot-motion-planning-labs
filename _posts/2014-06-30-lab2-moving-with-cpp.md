---
layout: post
title: "Lab 2: Get Moving with C++"
description: This lab serves as an introduction to rostopic, catkin_make, ROS nodes, and a simple polygon trace motion.
zipFile: intro_to_motion.zip
---

I'll write an introduction here - Jezmin

Preliminaries
--------------

Using the instructions from the Getting Started lab, connect to the create base and launch the iRobot driver. The teleop keyboard will not be needed for this lab.

Introduction to topics and rostopic
-----------------

The rostopic command-line tool displays information about ROS topics. Currently, it can display a list of active topics, the publishers and subscribers of a specific topic, the publishing rate of a topic, the bandwidth of a topic, and messages published to a topic. The display of messages is configurable to output in a plotting-friendly format. 

* To see all running topics, run the following command:
    $ rostopic list

* You should see something like the following:


      /mobile_base/commands/velocity
      /mobile_base/sensors/core
      /mobile_base/sensors/imu_data
      /mobile_base/sensors/imu_data_raw
      /mobile_base_nodelet_manager/bond
      /odom
      /robot_pose_ekf/odom_combined
      /rosout
      /rosout_agg
      /tf
      /tf_static
      /turtlebot/incompatible_rapp_list
      /turtlebot/rapp_list
      /turtlebot/status
      /turtlebot_node/parameter_descriptions
      /turtlebot_node/parameter_updates
      /zeroconf/lost_connections
      /zeroconf/new_connections

* To see the information from the topic (for example, velocity) we can use the 
  following command:

      $ rostopic echo /mobile_base/commands/velocity

* If the robot is currently stationary, you should see something like this:

      linear:
        x: 0.0
        y: 0.0
        z: 0.0
      angular:
        x: 0.0
        y: 0.0
        z: 0.0

* We can publish to a topic, for example:

      $ rostopic pub /mobile_base/commands/velocity geometry_msgs/Twist “linear:
        x: 1.0
        y: 0.0
        z: 0.0
      angular:
        x: 0.0
        y: 0.0
        z: 0.0”
        
This should change the velocity of the robot. This shows an alternative way to 
  control the robot directly without using a node.

Catkin_make
-----------------

cd = change directory (lets you change the directory you are in at terminal)
ls = lists the folders in the directory
catkin_make = compiles → creates build/ devel/ folders
  builds packages
  call catkin_make after every changes made in the code
  call catkin_make in the root of your catkin workspace
catkin workspace = directory that contains your package which contains your nodes 
 which are your codes    


ROS nodes in C++
-----------------

We have provided a sample ROS C++ node that publishes velocity commands in order
 to move in a square. This publishes the same topics from part B above. First 
 download the zip file and extract into your catkin workspace. Running 

    $ catkin_make 

 from your workspace will compile your starter code and you should be able to run
 the sample program using 

    $ rosrun lab2_pkg lab2_node

 Note: The code written was written on just one iCreate. Each robot may be calibrated slightly
 differently, so if your robot does not make a perfect square, do not be alarmed,
 this will not affect your ability to complete the challenge. How have we done this? 
 Possibly, we wrote a code that went straight and turned 90 degrees, and then copied 
 and pasted it four times within a single function. Take a look at the goRobotGo 
 function in iRobot.h, using this code, change the velocity code and timing to 
 move the robot in different patterns (circle, triangle, hexagon). 
