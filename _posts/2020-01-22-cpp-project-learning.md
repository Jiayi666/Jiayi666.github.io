---
layout:     post
title:      "C++ Project Learning"
subtitle:   "FUSE based File System"
date:       2020-01-22
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - C/C++
    - File System
---

#### FUSE Resources

- [libfuse home page](https://libfuse.github.io/)
- [NMSU - Writing a FUSE Filesystem: a Tutorial](https://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/)

### C/C++ Operations

#### Terms

- POD type : A Plain Old Data Structure in C++ is an aggregate class that contains only PODS as members, has no user-defined destructor, no user-defined copy assignment operator, and no nonstatic members of pointer-to-member type. See [this question](https://stackoverflow.com/questions/146452/what-are-pod-types-in-c) for more details.

#### Memory Allocation

> `memset` vs `new` vs `malloc` !

&nbsp;&nbsp;&nbsp;&nbsp;