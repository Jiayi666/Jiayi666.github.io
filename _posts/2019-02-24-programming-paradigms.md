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

> Analyzing your algorithm with **online/offline** ande **stable/unstable** operation. Check [this answer](https://leetcode.com/problems/k-closest-points-to-origin/discuss/220235/Java-Three-solutions-to-this-classical-K-th-problem.) that using global sort is an offline algorithm because it needs to know all the values for the operation but max-heap is an online method since it can use heapify to insert new items.

### Devide and Conquer

&nbsp;&nbsp;&nbsp;&nbsp;By looking at algorithms for Merge Sort, Quick Sort and [Closest pair of points](https://en.wikipedia.org/wiki/Closest_pair_of_points_problem), the major advantage/drive for using devide and conquer is actually to **save the apparently unnecessary search**. In algorithm from the above link, we eliminated the search between points that has more than one split lines between them.

&nbsp;&nbsp;&nbsp;&nbsp;And by using devide and conquer, we normally can change our complexity from `O(N)` to `O(logN)` just like binary search did.

#### Binary Search

&nbsp;&nbsp;&nbsp;&nbsp;Binary search is so important, it's implementation should also be carefully remembered. Check [this problem](https://www.geeksforgeeks.org/binary-search/) to see that the most efficient implementation for binary search is by **sliding window**. And the return for binary search should be one side of the window or mid.

### BackTracking

> The backtracking algorithm is basically equal to keep track of **the path in DFS**.

&nbsp;&nbsp;&nbsp;&nbsp;According to [this tutorial](https://www.geeksforgeeks.org/backtracking-algorithms/), the main idea for backtracking is to **detect failure ASAP**. 

&nbsp;&nbsp;&nbsp;&nbsp;In backtracking, we just recursively build/enumerate all ways that may lead to a solution and abort whenever a conflict appears. Check the [N Queen Problem](https://www.geeksforgeeks.org/n-queen-problem-backtracking-3/) and [this leetcode problem](https://leetcode.com/problems/letter-combinations-of-a-phone-number/solution/).

&nbsp;&nbsp;&nbsp;&nbsp;Take a look at [this problem](https://leetcode.com/problems/permutations/discuss/18296/Simple-Python-solution-(DFS).), the implementation of backtracking is equal to **use the path from DFS**. We only add the result to the list when we are sure the result is correct.

### Dynamic Programming

> Any recurssion algorithm should be solved with DP. The process of recurssion is just push to stack and pop latter, we can use DP to eliminate the stack operation.

> [This solution](https://leetcode.com/problems/jump-game/solution/) perfectly demonstrated how to optimize a recurssive algorithm and finally get an even better algorithm than just DP.

&nbsp;&nbsp;&nbsp;&nbsp;In my [previous post](https://jiayi666.github.io/2019/02/17/leetcode-google3/) and [this](https://jiayi666.github.io/2019/02/25/google11/), I described the normal process and major elements for using DP as:

1.	Identify if it is a DP problem
2.	Decide a state expression with 
   least parameters
3.	Formulate state relationship    
4.	Do tabulation (or add memoization)

&nbsp;&nbsp;&nbsp;&nbsp;This [problem](https://leetcode.windliang.cc/leetCode-10-Regular-Expression-Matching.html) and [this problem](https://leetcode.windliang.cc/leetCode-44-Wildcard-Matching.html) shows the use of **two dimensional DP**. In the above problem, the states are defined in two dimension and the tabular for DP is represented by an array. This described a new way of representing **hard to follow** state transitions.