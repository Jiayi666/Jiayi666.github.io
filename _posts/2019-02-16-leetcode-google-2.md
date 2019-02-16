---
layout:     post
title:      "LeetCode Prepare for Google - Day 2"
subtitle:   "Hash Table, Linked List, Math"
date:       2019-02-16
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

> Consider all situations for testing! Especially input is `None`.

> Analyze array/linked-list problems in a **pointer** view, any array problems including comparing, subtraction should require at least two pointer that keep track of two entities.

### To Do 
* Tree
* Dynamic Programming

### Python Programming

* Sort and list is just as simple as `list.sort()` and there will be no return and the list is sorted within `O(nlogn)`.
* Use `for i,j in zip(lis1, lis2)` to get items from two list at the same time. If the two lists are in different length, the for loop will stop when one list ends.
* To reverse a list with `list.reverse()`, to reverse a string with `str[::-1]`.
* Any number is grater than `None` in python, `-99999 > None` is true.
* Python list insert `list.insert(index, element)`.

### LeetCode Problems

#### 53 Maximum Subarray **??**

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/maximum-subarray.py), I haven't think through how to analyze problems like this. For now, I just think we need to consider the *special cases*, in this problem is there are only negative or positive intergers.

&nbsp;&nbsp;&nbsp;&nbsp;This is classified as *dynamic programming*, take a look.

#### 21 Merge Two Sorted List'

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/merge-two-sorted-lists.py), the algorithm isn't hard, but I also need to **get familiar with data structure**! For example, we need another pointer *curr* to indicate the current node while keeping head static to represent head of the list.

#### 206 Reverse Linked List

&nbsp;&nbsp;&nbsp;&nbsp;Be open mind, **we can use assistant functions**.

#### 141 Linked List Cycle

&nbsp;&nbsp;&nbsp;&nbsp;I used 'reverse' to solve this problem, even I don't know the Floyd's algorithm before, but I can give a reasonable answer by thinking about **what kind of operation we can do to a linked list**?

#### 121 Best Time to Buy and Sell Stock

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/best-time-to-buy-and-sell-stock.py), for the data structure of array, we need to alert with the **serial/order** attribute. In this problem we are using an array as an abstraction for time series data.

&nbsp;&nbsp;&nbsp;&nbsp;Also, don't give yourself more requirement than needed! We don't need to keep track of where is the best price come from.

&nbsp;&nbsp;&nbsp;&nbsp;For some problem, it may be better to focus on **local** instead of **global**. This is two things we can consider during analyze a problem.

#### 88 Merge Sorted List

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://github.com/Jiayi666/LeetCode/blob/master/Python/merge-sorted-array.py), I found it is easier to think programming problems in the **pointer, data structure** way.

&nbsp;&nbsp;&nbsp;&nbsp;To deal with array problems that including comparing, adding, subtraction (121, the above problem), the first thing we though about is that we need **two pointer** to keep track of two entity for comparing or subtraction.