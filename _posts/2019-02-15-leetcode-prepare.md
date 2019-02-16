---
layout:     post
title:      "LeetCode Prepare for Google - Day 1"
subtitle:   "Hash Table, Linked List, Math"
date:       2019-02-15
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

>You always need to solve the problem **by yourself, by intuition, by math** first. Then design algorithms and data structure based on math purpose.

### Python Programming

* `a or None` will directly return `a`, very useful in data structure like linked list.
* `map, reduce, filter` and `lambda` function must be used frequently.
* `ord` function will give unicode number for characters.
* `int` can directly transform string to int, but need to mind the **overflow**!
* Reverse a string with `str[::-1]`. This is in extend slice, where it works by doing `[begin:end:step]` - by leaving begin and end off and specifying a step of -1, it reverses a string.
* String can't be assigned value. For example `s = '123'; s[0] = '2'` is wrong.

### LeetCode Questions

#### 36 Valid Sudoku

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/valid-sudoku.py), in this problem, there are two things I learned.

&nbsp;&nbsp;&nbsp;&nbsp;First, analyze the problem clearly (brute-force but with **clear aim**). For the problem of valid sudoku, it is obvious that we need to check each critieria one after another, so the first step (**most outside layer**) would be taking each part of sudoku out. Then we need to find the filled part. And finally we want to check if the filled parts in each block have no repetition.

&nbsp;&nbsp;&nbsp;&nbsp;The second lesson is to choose data structure based on the task (**this also mean you need to think through the task very clearly**). Here, we want to know if the filled part in sudoku is *unique*, so we should use `set`.

#### 23 Merge K Sorted Lists

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/merge-k-sorted-lists.py), in this problem, it seems like **divide and conquer** should always been considered for any **k** times questions, such as [here](https://leetcode.com/problems/4sum/). Break down a *k problem* to *2 problem* is not only easier to program but also easier to think.

#### 2 Two Sum

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/two-sum.py), in this problem, I mainly take care of the first solution.

&nbsp;&nbsp;&nbsp;&nbsp;When we analyzing the problem, we should think about the **program paradigms** that we actually following in this problem! The problem of two sum is actually a **search** problem finding the complement for current number.

&nbsp;&nbsp;&nbsp;&nbsp;Also, we should think about and summarize the advantages and disadvantages for different data structures. Here we used hash table which is a tradeoff that used space to get time.

#### 13 Roman to Interger

&nbsp;&nbsp;&nbsp;&nbsp;The first thing to care about is not algorithm or data structure, is just to **solve/understand the problem** by myself (*without programming*). Only after we can analyze the problem clearly, can't we design algorithms.

#### 20 Valid Parenthesis

&nbsp;&nbsp;&nbsp;&nbsp;**You always need to solve the problem by yourself, by intuition, by math first**.