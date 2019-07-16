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

> Do check **leetcode articles** for deeper understanding of problems! Many articles are really well made.

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

#### 907. Sum of Subarray Minimums

> Take a look at [this article](https://leetcode.com/articles/sum-of-subarray-minimums/) about how to solve this problem.

> Caring about **hills** in an array is where stack can really be useful. This is called **increasing stack**.

&nbsp;&nbsp;&nbsp;&nbsp;The idea of using stack to find **monotonic properties** within an array is brilliant. Using stack, we can eliminate many *redundant operations (based on the monotonic property)*.

&nbsp;&nbsp;&nbsp;&nbsp;Considering that our task is to find the smallest index `i <= j` for which `A[i], A[i+1], ..., A[j] are all >= A[j]`. So, our focus should be the first leftside element that is smaller than `A[j]`. As a result, we can only care about **down going hills**! Caring about **hills** in an array is the most commom senario we can leverate a stack.

> [This tutorial](https://leetcode.com/problems/sum-of-subarray-minimums/discuss/170750/C++JavaPython-Stack-Solution) gives pretty good analysis from instinct to how we can solve the problem.

&nbsp;&nbsp;&nbsp;&nbsp;One of the most important thing to think for programming problems is **what is used with repeatition!** Here, every subarray is just used once, but every elements is used multiple times (in different subarraies). As a result, the instinct should be *go through the element just once*.

&nbsp;&nbsp;&nbsp;&nbsp;Also, when we are talking about **potential of improvement**, no matter if the first impression is to go through the elements or the subarraies, it is clear that go through all the subarries has no room for improvement because itself is already a `O(N^2)` operation.