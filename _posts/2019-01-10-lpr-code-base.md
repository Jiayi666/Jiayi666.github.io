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

### Minimum Required System

&nbsp;&nbsp;&nbsp;&nbsp;For most of our project we don't need all features built by previous lab members. To stablely lauch ubot in Gazebo, we only need `catkin_make --pkg ubot6 umass_sim_models (+ everything inside /catkin/src/third_party/gazebo_ros_pkgs, this is cloned by follow ros_setup_indigo.readme.txt)`.

### Gazebo

>[This](http://gazebosim.org/tutorials/browse) is the official tutorial for Gazebo, search for `ROS` in that page, there are a lot of ROS related tutorials.

>Also, [this tutorial](https://www.generationrobots.com/blog/en/robotic-simulation-scenarios-with-gazebo-and-ros/#create%20a%20Gazebo%20world) go through the whole process of building and using robot models in ROS and Gazebo from completely scratch. This is very useful, gives a lot of understanding for `urdf` files, `yaml` files and all the connection behind them. The source code for the above tutorial can be found [here](https://github.com/HumaRobotics/mybot_gazebo_tutorial).

#### Load the URDF for ubot6
> Some foundamental knowledge about gazebo is important, [this tutorial](https://www.generationrobots.com/blog/en/robotic-simulation-scenarios-with-gazebo-and-ros/) is a very good start to know about the relation between ROS, Gazebo and robot models.

* The most important thing: **read log files** if there is one! log files are very different compared with screen output!

&nbsp;&nbsp;&nbsp;&nbsp;One problem I met when try to load the ubot6 model to gazebo is the `gzserver: double free or corruption` when launching `roslaunch ubot6 gazebo_stand.launch`.

&nbsp;&nbsp;&nbsp;&nbsp;By following the above tutorial about ROS and Gazebo, I built my own simple environment with the URDF file for ubot6. By looking at the log file, I found the problem always happens at the process of building *TCP/IP connections*. In the URDF file, there is a line about `urdf/gazebo_plugins/ubot6.transmissions.xacro`. After comenting this line, gazebo works ok when including the ubot6 model.

#### Simulation Tutorials

&nbsp;&nbsp;&nbsp;&nbsp;One good simulation and real robot setting instruction can be found `/catkin/src/ubot/ubot_assembly/README.txt`. Another instruction can be found in `/catkin/src/umass_mode/Readme`.

#### Pause & Unpause Simulation

&nbsp;&nbsp;&nbsp;&nbsp;According to the file `roscd ubot6/launch/gazebo.launch` the gazebo server is start paused, detail can be find [here](http://gazebosim.org/tutorials?tut=ros_roslaunch) and [here](https://github.com/ros-simulation/gazebo_ros_pkgs/issues/291), both `-u` and `-paused` is set to pause the gzserver.

&nbsp;&nbsp;&nbsp;&nbsp;For how to **unpause** the simulation, check [this tutorial](http://gazebosim.org/tutorials/?tut=ros_comm). The command is `rosservice call gazebo/unpause_physics`. After using the above command, `ubot6/gui.launch` can now show robot state and control the robot.

### How to debug & Learn ROS

#### How to Learn a new package

&nbsp;&nbsp;&nbsp;&nbsp;If possible, find the official reference or tutorial like [this](http://wiki.ros.org/joint_trajectory_controller) and also find an usage example like [this](http://wiki.ros.org/Robots/TIAGo/Tutorials/trajectory_controller). This can be very helpful for understanding, use the official tutorial as complementation for a specific usage example.

#### Use `rqt_graph`

&nbsp;&nbsp;&nbsp;&nbsp;Using `rqt_graph` is very convenient for analyzing the system, the command is `rosrun rqt_graph rqt_graph`.
