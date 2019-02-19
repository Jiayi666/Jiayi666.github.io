---
layout:     post
title:      "LeetCode Prepare for Google - Day 3"
subtitle:   "Dynamic Programming, Tree, Recursion"
date:       2019-02-17
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

> To get the brute-force algorithm, follow the transition of the problem! Follow the **states, actions, and goal!**

> Take care the **ending** of the iteration! See problem 122.

> Be careful using recurssion, think about it's meaning and try iteration and DP. See problem 33.

### To Do 
* (Done) Tree
* (Done) Dynamic Programming
* DFS, BFS (Recursive + Iterative)
* String (join, replace etc.)
* Binary Search (Search Algorithms)
* Tree travel!

### Dynamic Programming (DP)

> [This tutorial](https://www.geeksforgeeks.org/solve-dynamic-programming-problem/) is great for DP. Also, check the **Algo -> Algorithm Paradigms** in this website, which concluded all programming paradigms I can use.

> Think dynamically! Thinking the problem as a contineuously growing, evolving problem.

> Check the **discussion** in leetcode pages, try to understand **all the ways to solve a problem!**

&nbsp;&nbsp;&nbsp;&nbsp;Steps to solve a DP:

1.	Identify if it is a DP problem
2.	Decide a state expression with 
   least parameters
3.	Formulate state relationship    
4.	Do tabulation (or add memoization)

&nbsp;&nbsp;&nbsp;&nbsp;The idea of DP is to find the transition between state and **solve the easy problem** (by decrising the complexity of state) then use the trasition to solve complicated problems.

&nbsp;&nbsp;&nbsp;&nbsp;Also, take care about how to write code for DP. Basically, we will use a list to represent the values for multiple states.

&nbsp;&nbsp;&nbsp;&nbsp;Check [this tutorial](), memoization is just **store the calculated results for each state** and reuse them when needed. So, by using memoization, we still only calculate each state once! **Think about this when you try to use recurssion.**

### Python Programming

* Use the `operator` package for operator like xor `operator.xor`. Combine this with `reduce/map/filter`.
* Use `del` to delete local variables. Check [this link](https://stackoverflow.com/questions/6146963/when-is-del-useful-in-python). `del list[i]` is equal to `list.pop(i)`.
* `object or None` will return the object itself.
* `from collections import defaultdict` to use default dict that can add keys easily, check [this link](https://stackoverflow.com/questions/5900578/how-does-collections-defaultdict-work).
* Use `float('inf')` to represent infinity in python.

### LeetCode Problems

#### 695 Max Area of Island

&nbsp;&nbsp;&nbsp;&nbsp;This problem isn't hard as long as we think about DFS/BFS. So, the most important thing for solving this is the ability for **making abstraction for algorithms and problems**.

&nbsp;&nbsp;&nbsp;&nbsp;Also, be calm and choose each data structure based on the problem carefully. Here the `visited` is always been check for duplication, then a `set` is better than `list`.

#### 136 Single Number

&nbsp;&nbsp;&nbsp;&nbsp;This is a typical question that represent a unique way to manipulate arries.

#### 70 Climb Stairs

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/climbing-stairs.py), for this problem, I firstly need to know how they created the brute-force algorithm! Basicly the brute-forcce way is **follow the process of the problem**. Here, **pretend I'm the agent**, follow the **actions, goals** and just list all posible ways.

&nbsp;&nbsp;&nbsp;&nbsp;Once we have the brute-force algorithm, we can try to improve it. The basic ways including **there are some redundant calculation** or **there are unnecessisary calculation.**

#### 122 Best Time to Buy and Sell Stock II

&nbsp;&nbsp;&nbsp;&nbsp;[Link](), **take care the ending part!**

#### 33 Search in Rotated Sorted Array

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/search-in-rotated-sorted-array.py), check [my work](https://leetcode.com/problems/search-in-rotated-sorted-array/). **Give extra care for using recursion!** What is the right time to use recursion? Overlapping subproblem? Recurssion is computational expensive.

&nbsp;&nbsp;&nbsp;&nbsp;Check the process of [Quick Sort](https://www.geeksforgeeks.org/quick-sort/). Recurssion should happen when you split big problems into many subproblems. Here, we just *narrow down* the search space.

#### 167 Two Sum II - Input Array is Sorted

&nbsp;&nbsp;&nbsp;&nbsp;Check [this link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/discuss/51249/Python-different-solutions-(two-pointer-dictionary-binary-search).), this problem itself isn't hard, but there are multiple ways to solve this problem. In the future, I should try to understand all these ways to solve problems.

&nbsp;&nbsp;&nbsp;&nbsp;In the above link, check the **binary search** method, I didn't think in this way when I do this.