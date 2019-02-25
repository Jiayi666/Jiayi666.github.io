---
layout:     post
title:      "Programming Paradigms Summary"
subtitle:   "Greedy, DP, Devide and Conquer etc."
date:       2019-02-24
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### Devide and Conquer

&nbsp;&nbsp;&nbsp;&nbsp;By looking at algorithms for Merge Sort, Quick Sort and [Closest pair of points](https://en.wikipedia.org/wiki/Closest_pair_of_points_problem), the major advantage/drive for using devide and conquer is actually to **save the apparently unnecessary search**. In algorithm from the above link, we eliminated the search between points that has more than one split lines between them.

&nbsp;&nbsp;&nbsp;&nbsp;And by using devide and conquer, we normally can change our complexity from `O(N)` to `O(logN)` just like binary search did.

#### Binary Search

&nbsp;&nbsp;&nbsp;&nbsp;Binary search is so important, it's implementation should also be carefully remembered. Check [this problem](https://www.geeksforgeeks.org/binary-search/) to see that the most efficient implementation for binary search is by **sliding window**. And the return for binary search should be one side of the window or mid.