---
layout:     post
title:      "LeetCode Array"
subtitle:   "Array based algorithm and thinking methods"
date:       2018-12-16
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### Sorting Algorithm
> [This website](https://www.geeksforgeeks.org/sorting-algorithms/#algo) is a good place to learn some useful algorithms. The following information is mainly from this website.

##### Selection Sorting
&nbsp;&nbsp;&nbsp;&nbsp;The idea behind selection sort is very simple. In [this page](https://www.geeksforgeeks.org/selection-sort/), the selection sorting is just to select the minimum element in the array in each iteration. So the time complexity is `O(n^2)`.

&nbsp;&nbsp;&nbsp;&nbsp;Implementation notification:

* **Space complexity** should be considered in array operation. A lot of time, if we can do **swap** in an array, we can eliminate the space consumption for making an temporary array. For example, in selection sorting, we can always swap the minimum element with the `head` of current array and move the `head` to the next index.

##### Bubble Sorting
&nbsp;&nbsp;&nbsp;&nbsp;Bubble sorting has the same complexity as selection sorting in worst case, but has linear complexity in best case.

##### Merge Sorting
&nbsp;&nbsp;&nbsp;&nbsp;Merge sorting has the same time complexity with Quick sorting, which is `O(nlog(n))`.

&nbsp;&nbsp;&nbsp;&nbsp;Compared with quick sorting, merge sorting **sort when merge**, while quick sorting **sort when partition**. They share the same idea of **divide and conquer**.

&nbsp;&nbsp;&nbsp;&nbsp;As shown in [here](https://www.geeksforgeeks.org/merge-sort/), merge sorting use equal divide to build a tree and sort two element when merging the tree.

&nbsp;&nbsp;&nbsp;&nbsp;In the implementation, space complexity should also be concerned. For the code in the website, all operation is directly put on the array and this idea is very compatable with the recursive algorithm.

##### Quick Sorting
&nbsp;&nbsp;&nbsp;&nbsp;The most widely used sorting algorithm. Check [this page](https://www.geeksforgeeks.org/quick-sort/) for detail.

&nbsp;&nbsp;&nbsp;&nbsp;Quick sorting **sort array when partition**. In each partition, the elements smaller than pivot is swapped to former array, elements larger than pivot is swapped to later array. This is also a way to build a binary tree just like merge sorting and the leaves of the tree is already the result.

### LeetCode Problems

#### 11. Container with Most Water
&nbsp;&nbsp;&nbsp;&nbsp;The definition of the problem can be found [here](https://leetcode.com/problems/container-with-most-water/). 

##### How to analyze the problem
1. It is apparent that if we want to find the optimal solution, we must compare **all** possible combinations. So, a nested iteration is needed.
2. **Is there anyway we can accelerate the nested iteration?** We are not expected to find the mathematical solution that can directly find the optimal solution, but we should **use 'easy to see' math property to reduce the needed search**.

##### Solution and think
&nbsp;&nbsp;&nbsp;&nbsp;The solution of this problem can be found [here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#lists).

&nbsp;&nbsp;&nbsp;&nbsp;The main problem here is to eleminate search as many as possible. In the problem, all height is interger and the coordinate is discrete, so it is efficient to only move the short side and eleminate the calculation of area with decreasing short side.

#### 15. 3Sum
&nbsp;&nbsp;&nbsp;&nbsp;This problem can be found [here](https://leetcode.com/problems/3sum/).

##### How to analyze this problem
&nbsp;&nbsp;&nbsp;&nbsp;The idea is still the same with before: **use brute force method as baseline and try to use mathematical tricks to improve**. How to find the mathematical way? It is related with how to find the **algorithm abstraction** for this problem.

&nbsp;&nbsp;&nbsp;&nbsp;In this problem, a possible **algorithm abstraction** is `search` paradigm. Once we have determined two numbers, it is a search problem for us to find the possible third number.

&nbsp;&nbsp;&nbsp;&nbsp;The inspiration for algorithm abstraction is the brute force method. In this problem, because in brute force way, we need to use 3 nested loop, so it is normal to think about the most inner loop where other 2 numbers have been determined.

##### Solution and think
&nbsp;&nbsp;&nbsp;&nbsp;It is very interesting to check different solutions. Like solution [here](https://github.com/qiyuangong/leetcode/blob/master/python/015_3Sum.py) completely did what I said **use brute force as guideline and use 'math' / 'algorithm abstraction' to simplify the brute force** method.

&nbsp;&nbsp;&nbsp;&nbsp;On the solution [here](https://github.com/haoel/leetcode/blob/master/algorithms/cpp/3Sum/3Sum.cpp), except for the above solution, they also used a hash map to accelerate. This is about to analyze if this is a time constrained problem or space constrained problem, also used more algorithm abstraction.
