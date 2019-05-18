---
layout:     post
title:      "LeetCode Prepare (Summer 2019) -- Day 05"
subtitle:   ""
date:       2019-05-09
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

#### 609. Find Duplicate File in System

&nbsp;&nbsp;&nbsp;&nbsp;In [this answer](https://leetcode.com/problems/find-duplicate-file-in-system/discuss/104123/C%2B%2B-clean-solution-answers-to-follow-up), using *multi-layer filter* for large files can't been hash is a good design pattern I can learn.

#### 528. Random Pick with Weight

> Again, firstly think about **what you need** then about how to do it (what data structure algorithm etc.)

&nbsp;&nbsp;&nbsp;&nbsp;In this problem, mapping an interval to a key is very similar as decision tree. In [this answer](https://leetcode.com/problems/random-pick-with-weight/discuss/154076/Python-binary-search-solution) we can see that *using a BST in array is just binary search!*

&nbsp;&nbsp;&nbsp;&nbsp;When we use binary search, we don't need any other criteria than `l<r` because at the end, `l==r` and both of them pointing to the answer we searched for.

#### 394. Decode String

> **Start with simple cases** and analyze the *state* and *features* we used in this problem!

&nbsp;&nbsp;&nbsp;&nbsp;Don't let data structure & algorithm influenced your **analyze of the problem**! Think about the problem, *what is the feature we need to care, what is the state and transition in this problem*?

&nbsp;&nbsp;&nbsp;&nbsp;Analyze should **start with simple cases**, in this problem, start without recursion can help us to know the structure for simplest state & features! Start with complex cases is likely to make you lost!

