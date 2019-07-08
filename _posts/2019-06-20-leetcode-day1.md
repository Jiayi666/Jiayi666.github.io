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
---

> Analyze programming problems like physical problems! Data Structure is the **model**, the methods (operations) we can do on this data structure is the **dynamics**.

> We may should always analyze programming problem as **sequence of states**, which is exactly how program works. And only the ones that the current state is based on previous state, dynamic programming should be considered.

### Java Programming

- `int minVal = Integer.MIN_VALUE` is the way to assign an integer with the minimum value in Java Integer class. `Integer.MAX_VALUE` is for maximum value.
- `string.split(regex,limit)`, check [here](https://www.geeksforgeeks.org/split-string-java-examples/) for more detail about `limit` parameter.
- The *default value* for integer array is all `0` guarantted.
- It is possible to change the `i` during a for loop, it seems like the for loop is just implemented by adding `i` by 1 in ever loop.
- You can't declear the length of an array untill you actually build it! `int[] a = new int[10];`, you can't say `int[10] a;`.
- There is no *default parameters* in Java, use **constructor chaining** instead.

### Interesting Problems

#### 51. N-Queens

&nbsp;&nbsp;&nbsp;&nbsp;Using `x+y` and `x-y` to process **lines in array** is a normal idea in array operations! Must practice and keep aware of this.

#### 55. Jump Game

&nbsp;&nbsp;&nbsp;&nbsp;Just to write down it again: Top-Down dynamic programming is called **memoization**, it reason is to **memorize** information that can be used by **each state** (a little bit like Markov property, the information is only related with the state itself, not about how we get to that state.)

&nbsp;&nbsp;&nbsp;&nbsp;The Bottom-Up dynamic programming is called **Tabulation** which should be understood as building up a table directed by the **recursive relation** between states.

#### 60. Permutation Sequence

&nbsp;&nbsp;&nbsp;&nbsp;Always **try several examples!** In this problem, `k-=1` is the key, it is easy to see if you try to run your code in several easy (especially **initial cases**).

#### 61. Rotate List

&nbsp;&nbsp;&nbsp;&nbsp;There are two ways of thinking about a programming problem. The first is to follow the problem **step by step**. The second is by observing the start and end to analyzing the influence of **a bunch of operations**.

&nbsp;&nbsp;&nbsp;&nbsp;In this problem, step by step solution means actually rotate the linked list `k` times. Observing start and end means rotate the linked list by the pivot! This also reminds the importance of actually **try some examples**!

#### 975. Odd Even Jump

&nbsp;&nbsp;&nbsp;&nbsp;A hard level problem is normally containing **more than one layer**. For example, in this problem, using dynamic programming is easy to get but this isn't the end! It just **reudced the problem** to another problem needs to be solved.

