---
layout:     post
title:      "Abstractive Features for Data Structures Summary"
subtitle:   "HashSet, HashTable, Tree, Graph, Array etc."
date:       2019-02-24
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### Hash Table

&nbsp;&nbsp;&nbsp;&nbsp;As in [this problem](https://leetcode.com/problems/copy-list-with-random-pointer/discuss/43485/Clear-and-short-python-O(2n)-and-O(n)-solution), hash table is actually building a **one-to-one mapping** between any two space! The key can be any object, so does the values.

### Hash Set

&nbsp;&nbsp;&nbsp;&nbsp;Hash set in python is just `set(xxx)`. Unlike hash table, hash set doesn't care what is the value for each key, it just care **if an element exists in the set**.

### Heap

> Python functions for creating/using heap (priority queue) is [here](https://www.geeksforgeeks.org/heap-queue-or-heapq-in-python/).

&nbsp;&nbsp;&nbsp;&nbsp;Heap is a data structure good at **sorting/priority**. Heap is mainly used to represent a **priority queue** like [here](https://www.geeksforgeeks.org/heap-queue-or-heapq-in-python/). 

&nbsp;&nbsp;&nbsp;&nbsp;The complexity for building a max/min heap is `O(nlogn)` while for building a binary heap is `O(n)`. See [here](https://www.geeksforgeeks.org/time-complexity-of-building-a-heap/) for more detail.

