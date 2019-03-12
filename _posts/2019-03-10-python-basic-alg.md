---
layout:     post
title:      "Python Implementation for Basic Algorithms"
subtitle:   "Sort, Search, Hash etc."
date:       2019-03-10
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### Sorting

#### Quick Sort

> Quick sort is to **sort while partition**.

&nbsp;&nbsp;&nbsp;&nbsp;As said above, the process for quick sort is to **call partition** then call quick-sort to both side after partition.

&nbsp;&nbsp;&nbsp;&nbsp;Take care, in python, slicing list will create a copy of the list! Pass by reference won't work. We have to use two pointer here.

#### Merge Sort

> Sort while merging.

&nbsp;&nbsp;&nbsp;&nbsp;First partition the list by its middle point (no comparing, just `(lo+hi)//2`). Then iteratively call merge-sort to both parts of the partition. Finally combine the two sorted part to one list.

