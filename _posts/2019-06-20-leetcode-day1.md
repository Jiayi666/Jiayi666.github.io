---
layout:     post
title:      "LeetCode Daily Day1"
subtitle:   ""
date:       2019-06-20
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

> Analyze programming problems like physical problems! Data Structure is the **model**, the methods (operations) we can do on this data structure is the **dynamics**.

### Java Programming

- `int minVal = Integer.MIN_VALUE` is the way to assign an integer with the minimum value in Java Integer class. `Integer.MAX_VALUE` is for maximum value.
- `string.split(regex,limit)`, check [here](https://www.geeksforgeeks.org/split-string-java-examples/) for more detail about `limit` parameter.
- The *default value* for integer array is all `0` guarantted.
- It is possible to change the `i` during a for loop, it seems like the for loop is just implemented by adding `i` by 1 in ever loop.
- You can't declear the length of an array untill you actually build it! `int[] a = new int[10];`, you can't say `int[10] a;`.
- There is no *default parameters* in Java, use **constructor chaining** instead.

### Interesting Problems

#### 53. Maximum Subarray

&nbsp;&nbsp;&nbsp;&nbsp;