---
layout:     post
title:      "Caffe & PyCaffe Installation"
subtitle:   "OS X 10.12 / CPU Only / Anaconda Python"
date:       2018-08-10
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Python
    - Caffe
---

### Install Prerequisite

* No need to install CUDA and Xcode if using CPU only mode.
* Install Anaconda before Homebrew.
* Use Homebrew to install all the dependency according to the [Caffe instruction](http://caffe.berkeleyvision.org/install_osx.html)

### Install Caffe

> With the official tool 'make'. 'cmake' is provided by community and I met some strange errors.

* Copy the `Makefile.config.example` to `Makefile.config`.
* Modify the `Makefile.config` as following:

1. Uncomment `CPU_ONLY := 1` to use CPU only mode.
2. Uncomment `USE_OPENCV := 0` `USE_LEVELDB := 0` and  `USE_LMDB := 0` to install the minimum interfate for caffe.
3. Uncomment and add `-std=c++11` to compiler `CUSTOM_CXX := g++ -std=c++11` to give C++11 support.
4. Change `BLAS := open` since we will use openblas according to the dependency we installed.
5. Comment the original `BLAS_LIB` and `BLAS_INCLUD` then uncomment the `BLAS_INCLUDE := $(shell brew --prefix openblas)/include` `BLAS_LIB := $(shell brew --prefix openblas)/lib` since we installed openblas by brw.
6. Comment the original `PYTHON_INCLUDE` and uncomment the `ANACONDA_HOME` and the `PYTHON_INCLUDE` with anaconda.
7. Change `PYTHON_LIB` to the anaconda version.
8. Uncomment `USE_PKG_CONFIG := 1`.

* Run `make caffe -j 4` to make caffe kernal with 4 threads.

### Runtest for Caffe

* It is very possible to meet the following error in `make runtest`:

```
.build_release/tools/caffe

dyld: Library not loaded: @rpath/libhdf5_hl.10.dylib

  Referenced from: /Users/work/gitclone/caffe/.build_release/tools/caffe

  Reason: image not found

make: *** [runtest] Abort trap: 6
```

According to [this page](https://www.cnblogs.com/mlj318/p/6478247.html), the right way to deal with this is to **添加libhdf5_hl.10.dylib所在路径添加到rpath** by running `install_name_tool -add_rpath '/Users/work/anaconda/lib'  /Users/work/gitclone/caffe/.build_release/test/test_all.testbin`.

### Install PyCaffe (the python interface)

* I met the following error:

```
ld: library not found for -lboost_python
clang: error: linker command failed with exit code 1 (use -v to see invocation)
make: *** [python/caffe/_caffe.so] Error 1
```

To deal with this, according to [this page](https://stackoverflow.com/questions/49961216/pycaffe-build-fails-lboost-python-not-found), the answer is:

1. vim Makefile (Take care, edit **Makefile**, not Makefile.config).
2. use vim command :?boost_python (there should only be 1 occurrence)
3. changed PYTHON_LIBRARIES ?= boost_python python2.7
      to PYTHON_LIBRARIES ?= boost_python27 python2.7
4. ran the command sudo make pycaffe

### Import Caffe in Python

* To import python, the last thing we need to do is **adding caffe to python path**. According to [this page](https://www.cnblogs.com/yizhichun/p/6339789.html), we should add to `~/.bash_profile` with `export PYTHONPATH=path_to_caffe/python:$PYTHONPATH` (Take care! Many answers says to add `path_to_caffe/python/caffe` and that won't work.)

### Import opencv installed by Homebrew at python

* According to [this page](http://answers.opencv.org/question/2413/problems-installing-opencv-on-mac-with-python/), the cv2.os file is stored in `/usr/local/lib/python2.7/site-packages/` and we need to add this address to PYTHONPATH.

