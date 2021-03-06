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

##### How to uninstall ROS
[Here](https://answers.ros.org/question/57213/how-i-completely-remove-all-ros-from-my-system/) is the instruction. Must remove ROS clearly before you start to compile everything again. The remaining from old version can hard a lot. **Remember to log out**, only after log out some cached ROS setting is removed. Most of the time, use `purge` seems to be more clearer than just `remove` if configuration file is not needed.

##### From ROS official website
&nbsp;&nbsp;&nbsp;&nbsp;Use `apt-get install` to install ROS package. The installed package will be automatically installed to `/opt/ros/share/`, which is the defaul ROS director.

&nbsp;&nbsp;&nbsp;&nbsp;In the ROS website, the display of package name and its inside is very wierd. For example, the **joystick_drivers** package is shown as `joystick_drivers:joy|ps3joy|spancenav_node|wiimote`. I have no idea what the latter part is, but if you want to install the package, just run `apt-get install ros-<ros version, such as indigo>-joystick-drivers`.

##### How to install ROS when Gazebo conflict
&nbsp;&nbsp;&nbsp;&nbsp;The gazebo version used in LPR is 6.7 and for indigo the default is gazebo 2.xx, so there will be a gazebo version conflict when you try to trinstall ROS in a lab pc. 

&nbsp;&nbsp;&nbsp;&nbsp;The method to override the existing gazebo is [this](https://blog.csdn.net/sinat_34816302/article/details/79145382).

`sudo aptitude install ros-indigo-desktop-full`

##### Protobuf version conflict
1. The problem of protobuf version conflict can be solve [here](https://github.com/BVLC/caffe/issues/6527). The main problem is 1. install version of protobuf too old. 2. packages installed by `apt-get` and from source is in different place and conflict with each other.
2. Error like this can directly check the file that leads to the error! There will be a header showing the required version of package. See instructions [here](http://answers.gazebosim.org/question/4733/this-file-was-generated-by-an-older-version-of-protoc-while-following-gazebo-tutorial/).
3. We can also go directly into the `CMakeCache.txt` file and vim search to quickly locate where is the packages used in cmake. This is also the case in `catkin_make`.

##### Compile Hardware first!
In the code base for LPR, there is a `makeLinux` file needs to be executed in Hardware file first! This will compile all the hardware package for ubot.

### CMake

##### Curl with CMake
&nbsp;&nbsp;&nbsp;&nbsp;The default CMake will make a copy of `libcurl` when it is compiled and `SSL` is disabled by default.

&nbsp;&nbsp;&nbsp;&nbsp;The way to compile CMake with SSL is [this](https://stackoverflow.com/questions/44633043/cmake-libcurl-was-built-with-ssl-disabled-https-not-supported). Remember to `make install`.

##### Don't uninstall CMake
&nbsp;&nbsp;&nbsp;&nbsp;It's completely a disaster to uninstall cmake. Because the os will automatically remove some ROS related files when uninstall cmake. Apparently the os think once you uninstall cmake those file won't useful too, which is not the case.

##### catkin make with `--force-cmake`
&nbsp;&nbsp;&nbsp;&nbsp;This is a very good way to do `catkin_make`. By using `--force-cmake`, we don't need to recompile something we already compiled before, but only focus on the "new" changes.

&nbsp;&nbsp;&nbsp;&nbsp;Also, sometimes when there are some conflicts in your code, just try several times of `--force-cmake`, it seems like the conflicts will be put at the end and other compilation will be solved first. And you are supposed to solve the confliction at very last of compiling. I'm even thinking maybe you can just start using the already compiled package and leave the part that has conflict along.

### Ubuntu

#### Terminal output
1. One very interesting problem is how to dump terminal output to a file, so you can get the unlimited scrolling and fast search for error and other information. The way to do that can be found [here](collect2: error: ld returned 1 exit status)
2. Search in vim can based on both direction. Like shown [here](http://vim.wikia.com/wiki/Searching). Use `?` to search forward while use `/` to search backward.
3. Use `tee` to print command output to stdout and a file a the same time. Instructions can be found [here](https://stackoverflow.com/questions/418896/how-to-redirect-output-to-a-file-and-stdout)

#### Package Conflict
