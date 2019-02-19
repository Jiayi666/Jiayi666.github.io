---
layout:     post
title:      "LeetCode Prepare for Google - Day 4"
subtitle:   "Tree, Python Time Complexity"
date:       2019-02-18
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### To Do
* (Done) DFS, BFS (Recursive + Iterative)
* String (join, replace etc.)
* Binary Search (Search Algorithms)
* Tree travesal!
* Python build-in functions, [link](https://docs.python.org/2/library/functions.html)

### Python Programming
* Check [this link](https://wiki.python.org/moin/TimeComplexity) for time complexity of python's basic types.
* Time complexity for check `item in set` is O(1) but `item in list` is O(n)!

### DFS & BFS

&nbsp;&nbsp;&nbsp;&nbsp;Check [this link](https://www.hackerearth.com/practice/algorithms/graphs/depth-first-search/tutorial/) for DFS and [this link](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/solution/) for BFS.

&nbsp;&nbsp;&nbsp;&nbsp;As can seen in the code from the above links, for BFS we keep a **queue** while for DFS we keep a **stack**! And most of the time the critieria for iteration is `while queue/stack not empty`.

&nbsp;&nbsp;&nbsp;&nbsp;Also, for DFS we normally can solve it with recursion.

### LeetCode Problems

#### 98. Validate Binary Search Tree

&nbsp;&nbsp;&nbsp;&nbsp;The normal way to trave through a tree is *DFS* or *BFS*. For how to choose between these two is by **using which I can find my goal quicker?**

#### 99. Recover Binary Search Tree

&nbsp;&nbsp;&nbsp;&nbsp;[Link](https://leetcode.com/problems/recover-binary-search-tree/discuss/32535/No-Fancy-Algorithm-just-Simple-and-Powerful-In-Order-Traversal), take care that **the DFS of a BST will return a sorted array!** To test the tree is valid, just test the the DFS array is correctly sorted.