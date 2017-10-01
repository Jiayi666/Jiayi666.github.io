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
