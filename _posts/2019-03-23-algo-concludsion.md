---
layout:     post
title:      "算法题思路总结"
subtitle:   "LeetCode刷题小结"
date:       2019-03-22
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

> We always **solve the problem first** then choose **alg & DS**.

&nbsp;&nbsp;&nbsp;&nbsp;

1. 如果没有任何idea／idea卡壳，先想想**brute force**。
2. It is so important to **get inspiration from test case**! 当想不到办法时写几个test case，进行具体的分析。

#### Searching

1. If we are searching a complicated structure (a series of number for example), we firstly need to define **what is the minimum part we need to search**, that is, what is the minimum part that will **determin** the complicated structure. In *Fibonachi Like series*, any two number in the series is enough to determine the whole series.