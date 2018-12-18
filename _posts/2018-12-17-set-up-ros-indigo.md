---
layout:     post
title:      "Set Up ROS Indigo"
subtitle:   "set up ROS in ubuntu 14.04"
date:       2018-12-17
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - ROS
---

### LPR ROS and Gazebo

#### How to install ROS package

##### From ROS official website
&nbsp;&nbsp;&nbsp;&nbsp;Use `apt-get install` to install ROS package. The installed package will be automatically installed to `/opt/ros/share/`, which is the defaul ROS director.

&nbsp;&nbsp;&nbsp;&nbsp;In the ROS website, the display of package name and its inside is very wierd. For example, the **joystick_drivers** package is shown as `joystick_drivers:joy|ps3joy|spancenav_node|wiimote`. I have no idea what the latter part is, but if you want to install the package, just run `apt-get install ros-<ros version, such as indigo>-joystick-drivers`.

#### How to install ROS when Gazebo conflict
&nbsp;&nbsp;&nbsp;&nbsp;The gazebo version used in LPR is 6.7 and for indigo the default is gazebo 2.xx, so there will be a gazebo version conflict when you try to trinstall ROS in a lab pc. 

&nbsp;&nbsp;&nbsp;&nbsp;The method to override the existing gazebo is [this](https://blog.csdn.net/sinat_34816302/article/details/79145382).

`sudo aptitude install ros-indigo-desktop-full`

### CMake

#### Curl with CMake
&nbsp;&nbsp;&nbsp;&nbsp;The default CMake will make a copy of `libcurl` when it is compiled and `SSL` is disabled by default.

&nbsp;&nbsp;&nbsp;&nbsp;The way to compile CMake with SSL is [this](https://stackoverflow.com/questions/44633043/cmake-libcurl-was-built-with-ssl-disabled-https-not-supported). Remember to `make install`.

### Ubuntu

#### Terminal output
1. One very interesting problem is how to dump terminal output to a file, so you can get the unlimited scrolling and fast search for error and other information. The way to do that can be found [here](collect2: error: ld returned 1 exit status)
2. Search in vim can based on both direction. Like shown [here](http://vim.wikia.com/wiki/Searching). Use `?` to search forward while use `/` to search backward.
3. Use `tee` to print command output to stdout and a file a the same time. Instructions can be found [here](https://stackoverflow.com/questions/418896/how-to-redirect-output-to-a-file-and-stdout)
