---
layout:     post
title:      "Linux Based File System - First Check"
subtitle:   "Linux Virtual File System (VFS), Linux Network File System (NFS)"
date:       2020-02-13
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - System
    - Linux
    - File System
---

### Linux FS 

#### Mount & Root File System

> [Root file system (rootfs)](https://superuser.com/questions/576723/what-is-rootfs-and-what-can-you-do-with-it)

&nbsp;&nbsp;&nbsp;&nbsp;Linux support multi-filesystem which means different FS (ext4, NFS, FAT32 etc.) can be used at the same time. The trick to achieve that is by using VFS and the concept of **mount**.

&nbsp;&nbsp;&nbsp;&nbsp;Every FS being used by the kernal must have a **mount point** in the **root file system (rootfs)**. Then, the kernal can manipulate data between different FS leveraging virtual file system described below.

### Linux VFS

> [Intro for linux VFS](https://opensource.com/article/19/3/virtual-filesystems-linux)

&nbsp;&nbsp;&nbsp;&nbsp;Virtual File System is a part of the system kernal and it works as an **abstraction layer** between the user and actual implementation of FS.

&nbsp;&nbsp;&nbsp;&nbsp;VFS is more like an interface and all the actual FS such as ext4, NFS, FAT32 must implement the declared system function `read()`, `write()`, and `open()`.

> [/proc file system](https://likegeeks.com/linux-virtual-file-system/)

&nbsp;&nbsp;&nbsp;&nbsp;The proc file system is widely used in linux. It's a VFS used for dealing with the kernel functionalities. We can use command like `cat /proc/cpuinfo` to check cpu status. Reach to the tutorial for more detail about proc FS.

### Linux NFS

> [Arch NFS](https://wiki.archlinux.org/index.php/NFS)
