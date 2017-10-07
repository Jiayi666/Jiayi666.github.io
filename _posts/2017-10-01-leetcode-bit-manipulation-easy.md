---
layout:     post
title:      "LeetCode: Bit Manipulation"
subtitle:   "(Easy)"
date:       2017-10-1
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
---

### 136 Single Number
Problem: Given an array of integers, every element appears twice except for one. Find that single one.
Note: Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

~~~python
import operator
class Solution:
    def singleNumber(self, nums):
    """
    :type nums: List[int]
    :rtype: int
    """
    return reduce(operator.xor, nums)
~~~
在leetcode中需要学习两个东西：(1)抽象的算法(2)具体的代码。需要学习某个算法适用的情况，甚至更深刻的，算法的思维过程。而代码则是工作中主要实现算法的工具。