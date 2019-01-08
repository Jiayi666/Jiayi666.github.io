---
layout:     post
title:      "Gazebo Simulator"
subtitle:   "Introduction to Gazebo and the ROS interface"
date:       2019-01-08
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - ROS
    - Simulation
    - Robotics
---

### Gazebo Server \& Client

&nbsp;&nbsp;&nbsp;&nbsp;The book "Learning robotics using python", the link ofwhich can be find in my last post, provided pretty good introduction that combines the use of ROS and gazebo.

&nbsp;&nbsp;&nbsp;&nbsp;When you run `rosrun gazebo_ros gazebo`, it is equal to run both `gzserver` and `gzclient` where the server is going to do the simulation while client deals with displayment.

#### How to check Gazebo with example

&nbsp;&nbsp;&nbsp;&nbsp;By using `roslaunch gazebo_ros mud_world.launch` to test the `gazebo_ros` package and use `gazebo \usr\share\gazebo\world\mud.world` to test the installation of gazebo itself. More detail can be found in [this question](https://github.com/ros-simulation/gazebo_ros_pkgs/issues/536). Also, in the above question, it shows that run `gazebo_ros` with `debug:=true` can sometimes change the problem of not showing anything and this method does work for me.

&nbsp;&nbsp;&nbsp;&nbsp;The official ROS interface for Gazebo can be found [here](http://gazebosim.org/tutorials/?tut=ros_roslaunch#Exampleroslaunchcommand).