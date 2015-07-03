---
layout: post
title: "Lab 2: Get Moving!"
description: This is another awesome lab!
zipUrl: https://github.com/gcc-robotics/robot-motion-planning-labs/archive/gh-pages.zip
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

* To see the information from the topic (for example, velocity) we can use the following command:

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
This should change the velocity of the robot. This shows an alternative way to control the robot directly without using a node.

