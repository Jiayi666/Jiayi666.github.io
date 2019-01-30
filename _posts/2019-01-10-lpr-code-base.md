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

&nbsp;&nbsp;&nbsp;&nbsp;For grasping, there is a tutorial in `roscd ubot_control/src/nodes/README`.

#### Pause & Unpause Simulation

&nbsp;&nbsp;&nbsp;&nbsp;According to the file `roscd ubot6/launch/gazebo.launch` the gazebo server is start paused, detail can be find [here](http://gazebosim.org/tutorials?tut=ros_roslaunch) and [here](https://github.com/ros-simulation/gazebo_ros_pkgs/issues/291), both `-u` and `-paused` is set to pause the gzserver.

&nbsp;&nbsp;&nbsp;&nbsp;For how to **unpause** the simulation, check [this tutorial](http://gazebosim.org/tutorials/?tut=ros_comm). The command is `rosservice call gazebo/unpause_physics`. After using the above command, `ubot6/gui.launch` can now show robot state and control the robot.

### How to debug & Learn ROS

#### How to Learn a new package

&nbsp;&nbsp;&nbsp;&nbsp;If possible, find the official reference or tutorial like [this](http://wiki.ros.org/joint_trajectory_controller) and also find an usage example like [this](http://wiki.ros.org/Robots/TIAGo/Tutorials/trajectory_controller). This can be very helpful for understanding, use the official tutorial as complementation for a specific usage example.

#### Use `rqt_graph`

&nbsp;&nbsp;&nbsp;&nbsp;Using `rqt_graph` is very convenient for analyzing the system, the command is `rosrun rqt_graph rqt_graph`. Remember to see the `Nodes/Topics (all)` mode instead of the default `Nodes Only` mode, it will show much more information.

## Ubot Controllers

### The `ros_control` packages

&nbsp;&nbsp;&nbsp;&nbsp;In the launching file `ubot6 gazebo.launch`, we loaded several controllers from `ros_control` package from `.yaml` file. This is the lowest level PID controller provided by ROS. More details is shown below.

#### Real Robot with `ros_control`

&nbsp;&nbsp;&nbsp;&nbsp;[This tutorial](https://slaterobots.com/blog/5abd8a1ed4442a651de5cb5b/how-to-implement-ros_control-on-a-custom-robot) showed great instruction about how to use `ros_control` package in a real robot. `ros_control` package handles two things from that process:

* receiving the goals (effort, position, velocity, trajectory, etc.)
* running the PID controllers

&nbsp;&nbsp;&nbsp;&nbsp;ros_control **doesn't** know or handle:

* implementing hardware control (sending current to motors)
* reading hardware state

&nbsp;&nbsp;&nbsp;&nbsp;So, the part `ros_control` doesn't know is the **hardware interface** (hardware driver). For ubot, this part is implied by on board FPGA.

#### High Level control with `ros_control`

> The official reference for `ros_control` can be find [here](http://wiki.ros.org/ros_control) and for `joint_trajectory_control` can be find [here](http://wiki.ros.org/joint_trajectory_controller#Published_Topics).

&nbsp;&nbsp;&nbsp;&nbsp;For now, what I need is to **send command** by `ros_control` and this should be the most frequently used feature for `ros_control`.

### Controllers in LPR codebase

> In the LPR codebase, we don't need to control ubot with pure PID controller provided by `ros_control` package. Many previous student has created very useful high-level controller in `ubot_control` package.

#### The `ubot_control` package

&nbsp;&nbsp;&nbsp;&nbsp;In the codebase, `ubot_control` package provided controllers including `bimanual_endpoint_controller` and `grasp_controller`. See the file `catkin_ws/src/ubot/ubot_assembly/launch/startup_task.launch` for how to load those controllers from launch file. Also see `catkin_ws/src/umass_model/Readme`, in this file follow it's instruction for start simulation, this will launch the bimanual position control from terminal. Don't forget to `rosservice call gazebo/unpause_physics` to see the simulation result.

#### Grasp controllers for ubot

&nbsp;&nbsp;&nbsp;&nbsp;In `roscd umass_model/Readme`, a combination of `endpoint position controller` and `bimanual grasp controller` are used. According to the code, what it did is just *reach both hand to certain pose and* **squeeze** towards the centroid of two hands.

&nbsp;&nbsp;&nbsp;&nbsp;In the package `ubot_grasp` there is a `composer.py` which should be the work left by Robert Platt which included moment residule, but I haven't figure out how to run it.