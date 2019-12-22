---
layout:     post
title:      "LeetCode EFS 01"
subtitle:   ""
date:       2019-12-20
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Interview
---

##### 935. Knight Dialer

&nbsp;&nbsp;&nbsp;&nbsp;This question is a great example of seeing a problem from **forward or backward**!

&nbsp;&nbsp;&nbsp;&nbsp;Also, it looks like we should always think about separating the program into **stages** and **transition function**.

##### 785. Is Graph Bipartite?

&nbsp;&nbsp;&nbsp;&nbsp;There are a few steps for solving a programming problem:

1. Analyze the problem and find a way of solving the problem **with natural language**. In this step, we need to understand the problem and think of analytical solution or programmatic solution (search). If no idea, using brute-force method should be considered in this step.
2. Find a programming **pattern** (Search? Traversal? Backtracking? DP? etc.) can fit the 'natural language solution'. Actually step 2 and step 1 are somewhat related because we can also use programming patterns to help finding the natural language solution.
3. See if we can do further optimization with some tricks such as shown in the following problem.

##### 837. New 21 Game

&nbsp;&nbsp;&nbsp;&nbsp;Thinking the brute-force method can really help us understand the problem. For this problem, the brute-force method takes exponential complexity and DP is a easily found better solution.

&nbsp;&nbsp;&nbsp;&nbsp;We can learn a trick from this problem : if we want to sum over an array, it can be simplified as `sum(m::n) = sum(1::n) - sum(1::m)`. This is especially usefull with DP.