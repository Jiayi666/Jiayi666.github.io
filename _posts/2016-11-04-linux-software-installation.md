---
layout:     post
title:      "Linux software installation"
subtitle:   "method to solve some commonly meet problems"
date:       2016-11-04
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	False
tags:
    - linux
---

### Normal steps to install third-party software
*	add the 'PPA' (personal package archive) to your "/etc/apt/source.list" file
*	use`sudo apt-get update`to update your software package list
*	`sudo apt-get install packagename`to install the package

### Problems and Solution

#### Packages can't be reached
一般来说，直接报错无法找到或安装`package`或`dependency`都是由于当前系统的`源`出现了问题，就是说`/etc/apt/source.list`中所指示的软件包列表无法获取。这时应当检查该文件中的源是否可用，一般在中国使用163，Aliyun等[ubuntu源](https://launchpad.net/ubuntu/+archivemirrors)是没有问题的。可以直接用vim替换掉原本的`ubuntu.com`部分为`Aliyun.com`等源。

#### `apt-get upgrade`卡在"0% [Connecting to security.ubuntu.com (2001:67c:1562::15)]"
Turns out this is an issue where connecting over IPv6 on some servers causes them to get stuck at this point. The fix is really simple.
*	Open `/etc/gai.conf`
*	Uncomment the following line:`# precedence ::ffff:0:0/96 100`


This will allow you to still use IPv6 but sets IPv4 as the precedence so that apt-get won’t get stuck.

#### `install package`后提示需要dependency但是xx package没有安装
在提示上述ERROR后可以使用`sudo apt-get -f install`来自动检测并安装上述需要的dependency，但必须要运行过上述安装命令后才能使用。

#### 如果按照上述方法upgrade还出现错误
可以尝试`sudo apt-get dist-upgrade`进行更新。
*	update：更新软件列表“信息”，包括版本，依赖关系；
*	upgrade：在不改变现有设置的情况下更新软件； 
*	dist-upgrade：会改变旧的配置文件和旧的依赖关系，比如升级系统时。