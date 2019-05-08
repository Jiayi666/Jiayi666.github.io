---
layout:     post
title:      "LeetCode Prepare (Summer 2019) -- Day 02"
subtitle:   ""
date:       2019-04-30
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

#### 895. Maximum Frequency Stack

&nbsp;&nbsp;&nbsp;&nbsp;Look at what **you care/need** in this problem. Plan the most convinient way for completing the task, you will always find a way to program but the best algorithm comes from the best way to solve the task.

#### 490. The Maze

&nbsp;&nbsp;&nbsp;&nbsp;To find the end of movement by `while 0 <= ni < len(maze) and 0 <= nj < len(maze[0]) and maze[ni][nj] != 1`. **Don't think too much about details when planning for high level algorithm**! This is actually require understanding of trade-offs between high level algorithms.

&nbsp;&nbsp;&nbsp;&nbsp;Bi-directional BFS can be applied only when *the problem can be solve from both end!* In this problem, we may not be able to get start point from destination!