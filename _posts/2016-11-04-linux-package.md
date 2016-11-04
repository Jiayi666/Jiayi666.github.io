---
layout:     post
title:      "Linux packages installation"
subtitle:   "especially focus in R"
date:       2016-11-94
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	False
tags:
    - linux
---

#### 如何找到所需dependency的上级package
*	检索[Ubuntu Packages](http://packages.ubuntu.com/)官方文档，可以使用dependency的名字或者相关关键字
*	这是别人的回答：我没有安装过软件，但上述网站查询效果不错
<pre>
		To install things with the "sudo apt-get install" command you need to know the exact name of the package. If you are not sure it is better to use the `Synaptic package manager` which has a search function. Synaptic appears under System > Administration in Lucid Lynx. 
		I am on Natty and just did a search in Synaptic. There is no package called curl-dev or libcurl-dev, however, there are three packages with names libcurl4-xxx-dev. The description is that "these files allow to build software with libcurl". You may try install these and see if it works. In Lucid the version number may be different (so instead of libcurl4 you may have some other number)
</pre>