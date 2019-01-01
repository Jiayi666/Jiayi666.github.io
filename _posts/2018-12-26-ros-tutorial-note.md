---
layout:     post
title:      "ROS Tutorial Learning"
subtitle:   "The note for learning most fundamental ROS system"
date:       2018-12-26
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - ROS
---

> The main information contained in this note is from the [official tutorial](http://wiki.ros.org/action/fullsearch/ROS/Tutorials?action=fullsearch&context=180&value=linkto%3A%22ROS%2FTutorials%22). And some overall concept is from [this](http://www.clearpathrobotics.com/assets/guides/ros/index.html) website, but the templates in this website is mostly out of maintanance and can't be run.

#### Setup ROS
&nbsp;&nbsp;&nbsp;&nbsp;ROS can only be set up in ubuntu. ROS Indigo version works on 14.04 and Hydro version works on 16.04.

&nbsp;&nbsp;&nbsp;&nbsp;In this note, I used the **ROS pre-installed virtualbox image** from [here](https://nootrix.com/diy-tutos/ros-indigo-virtual-machine/) and make all the experiments in virtual machine.

#### What is ROS? Why ROS?
&nbsp;&nbsp;&nbsp;&nbsp;For this problem, [this page](http://www.clearpathrobotics.com/assets/guides/ros/Intro%20to%20the%20Robot%20Operating%20System.html) gives the best explaination. ROS is an operating system and the most important function for ROS is to **enable easy communication between different ROS node** and the communication is scheduled and supported by ROS master node (ros core).

&nbsp;&nbsp;&nbsp;&nbsp;So, ROS is not about how to control a robot or how to percept the environment, but just a platform, a operating system that offers some important service to the robot control system.

### ROS File System
#### Catkin Workspace
&nbsp;&nbsp;&nbsp;&nbsp;A catkin workspace is a folder where you modify, build, and **install catkin packages**.

&nbsp;&nbsp;&nbsp;&nbsp;All ROS packages should be installed in a catkin workspace. The `catkin_make` operation I used to install `umass_lpr` is based on catkin workspace. `umass_lpr` is also a catkin workspace and all individual packages in the workspace is managed in [this](http://wiki.ros.org/catkin/workspaces) archive format.

&nbsp;&nbsp;&nbsp;&nbsp;To create a catkin workspace, only the `src` directory is needed. By calling `catkin_make` for the first time, the `CMakeList.txt` file will be created based on `src` folder. Remember to source the `devel/setup.bash` for using packages in this workspace in bash. Detail tutorials can be found [here](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).

&nbsp;&nbsp;&nbsp;&nbsp;The correct way to build and install a catkin workspace with or without `catkin_make` can be found [here](http://wiki.ros.org/catkin/Tutorials/using_a_workspace).

&nbsp;&nbsp;&nbsp;&nbsp;The meaning of `catkin_make` and parameters can be set is described in [here](http://wiki.ros.org/catkin/commands/catkin_make). One thing to note is that `catkin_make install` is optional, once we `source devel/setup.sh`, we can use the package **as if we have installed it**.

#### ROS Package
&nbsp;&nbsp;&nbsp;&nbsp;The most fundamental ROS software unit is a ROS package, a ROS package will contain the following files and archieve.

* **Packages**: Packages are the software organization unit of ROS code. Each package can contain libraries, executables, scripts, or other artifacts.

* **Manifests (package.xml)**: A manifest is a description of a package (a file in ROS package directory). It serves to define dependencies between packages and to capture meta information about the package like version, maintainer, license, etc...

&nbsp;&nbsp;&nbsp;&nbsp;To create a ROS package in a catkin workspace is not only make a folder, we need to call `catkin_create_pkg` command to specify the dependency and automatically create needed archives.

&nbsp;&nbsp;&nbsp;&nbsp;[This tutorial](http://wiki.ros.org/ROS/Tutorials/CreatingPackage) here explains all files related to build and install a ROS package line by line including the `package.xml` and `CMakeList.txt` file. Reach to this tutorial for how to edit these files for building and installing ROS packages.

### Ros Communication System

#### ROS Topic

&nbsp;&nbsp;&nbsp;&nbsp;ROS system is organized as an distributed operating system. It also contains the publish / subscribe paradigms. In ROS, the communication between nodes are not by direct message sending but by publish the information to a topic and the subscribers will know it. This may be better for asynchronous communication in ROS. For command about ROS topic, you can check [here](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics).

#### ROS Message

&nbsp;&nbsp;&nbsp;&nbsp;ROS message is the **actual messages** being passed by ROS topics. The publisher will `pub` ROS messages to the topic. Different ROS message have different `type` and most of the type is defined specifically for this topic. To check the type of a ROS message and publish ROS message, see [this tutorial](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics).