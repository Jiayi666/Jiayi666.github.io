---
layout:     post
title:      "LeetCode EFS"
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

> The purpose of DP is **reduce duplicated** calculations! So, once you noticed duplicated calculation in your algorithm, try to use DP.

&nbsp;&nbsp;&nbsp;&nbsp;Thinking the brute-force method can really help us understand the problem. For this problem, the brute-force method takes exponential complexity and DP is a easily found better solution.

&nbsp;&nbsp;&nbsp;&nbsp;We can learn a trick from this problem : if we want to sum over an array, it can be simplified as `sum(m::n) = sum(1::n) - sum(1::m)`. This is especially usefull with DP.

##### 742. Closest Leaf in a Binary Tree

&nbsp;&nbsp;&nbsp;&nbsp;When we face the case we need to *go backward* in a tree, *change it to a graph* can be a good idea. Because the action of going backward basically breaked the meaning of a tree structure, thus we can expand a tree to a more abstract structure that still preserved the relation between nodes.

&nbsp;&nbsp;&nbsp;&nbsp;Changing a tree representation to a graph breaks the *parent-children* relationship in tree. The *parent-children* relation can be constrains and also helpers. For example, when we search for the longest path from leaf to leaf, we can use the parent-children relation as a hint and use DP!

##### 373. Find K Pairs with Smallest Sums

&nbsp;&nbsp;&nbsp;&nbsp;For this question, it can be super helpful if you think about representing the result with matrix. But even if you don't, you can still do something to **minimize the cost** such as only consider the *first k element in both arrays*.

##### 1182. Shortest Distance to Target Color

&nbsp;&nbsp;&nbsp;&nbsp;This is a typical searching problem, and even the brute-force searching looks ok we may be able to improve that. The key of searching is to see **what is the critieria we are searching for** and **how we can get rid of candidates ASAP**. Using critieria as index is a good idea to get rid of candidates.

##### 1261. Find Elements in a Contaminated Binary Tree

&nbsp;&nbsp;&nbsp;&nbsp;In this problem we can see that we always have different ways of optimizing. Here we can calculate the path from root to the node which will cause `O(logN)` time complexity and `O(1)` extra memory. However, if we want to optimize for find latency, we can always use a set to store all nodes value.

&nbsp;&nbsp;&nbsp;&nbsp;Another point needs to learn from this problem is **make sure you understand what option is needed**, for example 'find existance', 'search with critieria' etc.

##### 1130. Minimum Cost Tree From Leaf Values

&nbsp;&nbsp;&nbsp;&nbsp;[This solution](https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/discuss/340004/Python-Easy-DP) is a typical **divide & conquer** method! If the result of mother problem can be divided into result of smaller problem, we should consider both **DP** and **divide & conqure**.