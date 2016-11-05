---
layout:     post
title:      "Linux packages installation"
subtitle:   "especially focus in R"
date:       2016-11-05
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	False
tags:
    - linux
---

#### R package 安装报错
　　在安装R packages时会遇到`ERROR: configuration failed for package ‘packagename’`的问题，要求安装新的Linux package提供支持。这一套过程在Windows系统中被后台默认执行了，在Linux中则需要手动安装相关packages，例如根据R的提示：
<pre>

		------------------------- ANTICONF ERROR ---------------------------
		Configuration failed because openssl was not found. Try installing:
 		* deb: libssl-dev (Debian, Ubuntu, etc)
 		* rpm: openssl-devel (Fedora, CentOS, RHEL)
 		* csw: libssl_dev (Solaris)
 		* brew: openssl (Mac OSX)
		If openssl is already installed, check that 'pkg-config' is in your
		PATH and PKG_CONFIG_PATH contains a openssl.pc file. If pkg-config
		is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
		R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
		--------------------------------------------------------------------
</pre>

安装相应的`libssl-dev`包，但是在安装package时可能遇到下面的问题。

#### 为什么会出现`package has no installation cadicade`错误

　　When you try to install a package using apt-get, APT searches it’s own database for the package name, if the package is available in the database, then it looks for the repository from where to download the package. It then download the package from that repository and installs it.
　　If the package name does not exist in APT’s database, it does not have any idea what you are trying to install and you see the error message above.
　　[这里](http://blog.163.com/liuzhuqing_508/blog/static/606213512012111311532835/)是关于这个问题的详细解释。解决方法可以通过下面介绍的从`Ubuntu Package Web`处查找所需的`deb`包并添加到`source.list`完成。

#### 如何找到所需dependency的上级package
*	检索[Ubuntu Packages](http://packages.ubuntu.com/)官方文档，可以使用dependency的名字或者相关关键字

	**注**:在检索到相关的package后转到**Download页面**可以看到提示下载相关package**所需的`deb`源位置**！！
*	这是别人的回答：我没有安装过Synaptic软件，但上述网站查询效果不错
<pre>
		To install things with the "sudo apt-get install" command you need to know the exact name of the package. If you are not sure it is better to use the `Synaptic package manager` which has a search function. Synaptic appears under System > Administration in Lucid Lynx. 
		I am on Natty and just did a search in Synaptic. There is no package called curl-dev or libcurl-dev, however, there are three packages with names libcurl4-xxx-dev. The description is that "these files allow to build software with libcurl". You may try install these and see if it works. In Lucid the version number may be different (so instead of libcurl4 you may have some other number)
</pre>