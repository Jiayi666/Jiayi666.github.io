---
layout:     post
title:      "Daily Programming Questions"
subtitle:   ""
date:       2019-10-22
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Java
    - Programming
    - Interview
---

#### 1062. Longest Repeating Substring

&nbsp;&nbsp;&nbsp;&nbsp;The key idea used in this question is:

- Iterate over *length of substring* instead of every char / substring in the string.
- Consider the iterating of length as a searching problem.

&nbsp;&nbsp;&nbsp;&nbsp;For the first part, iterate over every element in a container, especial ordered container, seems a steriotype we have in our programming. When dealing with programming questions, we should be aware of such steriotype and keep an eye on if it is possible to **targeting at the result directly**.

#### 429. N-ary Tree Level Order Traversal

&nbsp;&nbsp;&nbsp;&nbsp;This is a super easy BFS problem, but the challenging is *BFS with Java*. One big difference between Java and Python is that in Java **we can't put variable with different type into a single container / collection**.

&nbsp;&nbsp;&nbsp;&nbsp;The trick to solve this is to **make fully use of information onhand**. If the traversal is level by level, then if we keep track of the start and end of each level from the beginning, we can know the length of every level.

#### 901. Online Stock Span

&nbsp;&nbsp;&nbsp;&nbsp;Put more time on thinking what is the best way of solving the problem instead of struggling about implementation details.

&nbsp;&nbsp;&nbsp;&nbsp;Also, **take a second thought** before you start implementing. It's defenitely worth to take more time on planning. It can potentially make the implementation easier and save time too.

#### 686. Repeated String Match

&nbsp;&nbsp;&nbsp;&nbsp;Use **direct criteria for iteration!!!** Don't always get into the stereotype that loop over every element in the collection. Use critieria that directly show the **loop operation & check critieria** pattern.

&nbsp;&nbsp;&nbsp;&nbsp;Need more practice about language related tricks such as `"abc"*3 = "abcabcabc"` in python.