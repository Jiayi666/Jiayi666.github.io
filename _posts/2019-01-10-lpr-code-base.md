---
layout:     post
title:      "LPR Code Base"
subtitle:   "Problems and Notifications for LPR Code Base"
date:       2019-01-10
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - ROS
    - Simulation
    - Robotics
    - LPR
---

### Gazebo

#### Load the URDF for ubot6
> Some foundamental knowledge about gazebo is important, [this tutorial](https://www.generationrobots.com/blog/en/robotic-simulation-scenarios-with-gazebo-and-ros/) is a very good start to know about the relation between ROS, Gazebo and robot models.

* The most important thing: **read log files** if there is one! log files are very different compared with screen output!

&nbsp;&nbsp;&nbsp;&nbsp;One problem I met when try to load the ubot6 model to gazebo is the `gzserver: double free or corruption` when launching `roslaunch ubot6 gazebo_stand.launch`.

&nbsp;&nbsp;&nbsp;&nbsp;By following the above tutorial about ROS and Gazebo, I built my own simple environment with the URDF file for ubot6. By looking at the log file, I found the problem always happens at the process of building *TCP/IP connections*. In the launch file, there is a line about `urdf/gazebo_plugins/ubot6.transmissions.xacro`. After comenting this line, gazebo works ok when including the ubot6 model.