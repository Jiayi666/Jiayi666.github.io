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

- POD type : A Plain Old Data Structure in C++ is an aggregate class that contains only PODS as members, has no user-defined destructor, no user-defined copy assignment operator, and no nonstatic members of pointer-to-member type. A struct with no modifiers or methods is called a POD struct, which exists as a backwards compatible interface with C libraries as it is (supposedly) guaranteed to be laid out as though it were a C struct. See [this question](https://stackoverflow.com/questions/146452/what-are-pod-types-in-c) for more details. A `struct` is normally a POD type.

#### Memory Allocation

> `memset` vs `new` vs `malloc` !

&nbsp;&nbsp;&nbsp;&nbsp;`malloc` and `new` can actually allocate new memory space but `memset` can't. `memset` can only assign value for every byte in a memory space, most likely it will assign 0s.

&nbsp;&nbsp;&nbsp;&nbsp;The difference between `malloc` and `new` is that `malloc` **won't invoke constructor and destructor**. So, `malloc` is mostly for POD types while `new` is for C++ style types.