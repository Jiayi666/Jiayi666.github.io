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

### Setup ROS
&nbsp;&nbsp;&nbsp;&nbsp;ROS can only be set up in ubuntu. ROS Indigo version works on 14.04 and Hydro version works on 16.04.

&nbsp;&nbsp;&nbsp;&nbsp;In this note, I used the **ROS pre-installed virtualbox image** from [here](https://nootrix.com/diy-tutos/ros-indigo-virtual-machine/) and make all the experiments in virtual machine.

### What is ROS? Why ROS?
&nbsp;&nbsp;&nbsp;&nbsp;For this problem, [this page](http://www.clearpathrobotics.com/assets/guides/ros/Intro%20to%20the%20Robot%20Operating%20System.html) gives the best explaination. ROS is an operating system and the most important function for ROS is to **enable easy communication between different ROS node** and the communication is scheduled and supported by ROS master node (ros core).

&nbsp;&nbsp;&nbsp;&nbsp;So, ROS is not about how to control a robot or how to percept the environment, but just a platform, a operating system that offers some important service to the robot control system.

## ROS File System
### Catkin Workspace
&nbsp;&nbsp;&nbsp;&nbsp;A catkin workspace is a folder where you modify, build, and **install catkin packages**.

&nbsp;&nbsp;&nbsp;&nbsp;All ROS packages should be installed in a catkin workspace. The `catkin_make` operation I used to install `umass_lpr` is based on catkin workspace. `umass_lpr` is also a catkin workspace and all individual packages in the workspace is managed in [this](http://wiki.ros.org/catkin/workspaces) archive format.

&nbsp;&nbsp;&nbsp;&nbsp;To create a catkin workspace, only the `src` directory is needed. By calling `catkin_make` for the first time, the `CMakeList.txt` file will be created based on `src` folder. Remember to source the `devel/setup.bash` for using packages in this workspace in bash. Detail tutorials can be found [here](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).

&nbsp;&nbsp;&nbsp;&nbsp;The correct way to build and install a catkin workspace with or without `catkin_make` can be found [here](http://wiki.ros.org/catkin/Tutorials/using_a_workspace).

&nbsp;&nbsp;&nbsp;&nbsp;The meaning of `catkin_make` and parameters can be set is described in [here](http://wiki.ros.org/catkin/commands/catkin_make). One thing to note is that `catkin_make install` is optional, once we `source devel/setup.sh`, we can use the package **as if we have installed it**.

### ROS Package
&nbsp;&nbsp;&nbsp;&nbsp;The most fundamental ROS software unit is a ROS package, a ROS package will contain the following files and archieve.

* **Packages**: Packages are the software organization unit of ROS code. Each package can contain libraries, executables, scripts, or other artifacts.

* **Manifests (package.xml)**: A manifest is a description of a package (a file in ROS package directory). It serves to define dependencies between packages and to capture meta information about the package like version, maintainer, license, etc...

&nbsp;&nbsp;&nbsp;&nbsp;To create a ROS package in a catkin workspace is not only make a folder, we need to call `catkin_create_pkg` command to specify the dependency and automatically create needed archives.

&nbsp;&nbsp;&nbsp;&nbsp;[This tutorial](http://wiki.ros.org/ROS/Tutorials/CreatingPackage) here explains all files related to build and install a ROS package line by line including the `package.xml` and `CMakeList.txt` file. Reach to this tutorial for how to edit these files for building and installing ROS packages.

## Ros Communication System

### ROS Topic (Publication \& Subscription)

&nbsp;&nbsp;&nbsp;&nbsp;ROS system is organized as an distributed operating system. It also contains the publish / subscribe paradigms. In ROS, the communication between nodes are not by direct message sending but by publish the information to a topic and the subscribers will know it. This may be better for asynchronous communication in ROS. For command about ROS topic, you can check [here](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics).

#### ROS Message

&nbsp;&nbsp;&nbsp;&nbsp;ROS message is the **actual messages** being passed by ROS topics. The publisher will `pub` ROS messages to the topic. Different ROS message have different `type` and most of the type is defined specifically for this topic. To check the type of a ROS message and publish ROS message, see [this tutorial](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics).

#### How to code for ROS topic

&nbsp;&nbsp;&nbsp;&nbsp;As shown before, a ROS topic is just a pipeline for message (data) transfer in ROS system. This is a comparatively simple function and the only thing need to be defined before building a topic the **what message types are supported**.

&nbsp;&nbsp;&nbsp;&nbsp;To achieve the function for publication and subscription, we need to build two nodes, one talker (publisher) and one listenor (subscriber). The possible types for messages used in this topic is defined in a `.msg` file, for how to create a `.msg` file check [here](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv#Introduction_to_msg_and_srv). For detail tutorial about how to program for the talker and listener node can be found [here](http://wiki.ros.org/ROS/Tutorials/WritingPublisherSubscriber%28python%29).

### ROS Service

&nbsp;&nbsp;&nbsp;&nbsp;ROS service is another way to provide communication between ROS nodes. Instead of only publish and subscribe, using service (server / client paradigm) the user can define more complicated **server operation** compared with ROS topic. The command for ROS service is `rosservice` and the tutorial can be found [here](http://wiki.ros.org/ROS/Tutorials/UnderstandingServicesParams).

#### How to code for ROS Service (Server \& Client)

&nbsp;&nbsp;&nbsp;&nbsp;As shown above, a ROS service is defining a more complicated way to **process ROS message** instead of just publishing and subscribing raw messages. To define the behavior of a server, we need to define the **data type for requests and responds**.

&nbsp;&nbsp;&nbsp;&nbsp;The abstractive structure (data type for requests and responds) for a ROS service is defined in a `.srv` file, for how to make a `.srv` file check [here](http://wiki.ros.org/ROS/Tutorials/CreatingMsgAndSrv#Using_srv).

&nbsp;&nbsp;&nbsp;&nbsp;Both server and client need to import the `.srv` file for the ROS service to be used. The parameters passed to ROS service is **stored as a dictionary**, such as in [this tutorial](), `a, b` can be used as an element in dictionary `req` and `sum` is an element in dictionary `resp`.

#### Parameter Server (Global Parameters)

&nbsp;&nbsp;&nbsp;&nbsp;Most of the time, ROS parameter server is used to store **globally viewable parameters** such as configuration variables. Because this server is not designed to be high performance, the stored parameters should be static such as configuration parameters.

&nbsp;&nbsp;&nbsp;&nbsp;By using `rosparam`, user can load or dump data into the parameter server by variable name. Tutorials can be found [here](http://wiki.ros.org/Parameter%20Server).

### Message Generation Dependency