---
layout:     post
title:      "Abstractive Features for Data Structures Summary"
subtitle:   "HashSet, HashTable, Tree, Graph, Array etc."
date:       2019-02-24
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - LeetCode
    - Algorithm
    - Data Structure
---

### Python Basics

* When we make a slice of list, **a copy of the list is made!** For example, `x=[1,2,3]; a=x[:2]; a[0]=100`, the above assignment won't change the values in `x`!

### Hash Table

&nbsp;&nbsp;&nbsp;&nbsp;As in [this problem](https://leetcode.com/problems/copy-list-with-random-pointer/discuss/43485/Clear-and-short-python-O(2n)-and-O(n)-solution), hash table is actually building a **one-to-one mapping** between any two space! The key can be any object, so does the values.

### Hash Set

&nbsp;&nbsp;&nbsp;&nbsp;Hash set in python is just `set(xxx)`. Unlike hash table, hash set doesn't care what is the value for each key, it just care **if an element exists in the set**.

### Heap

> Because the building of max/min-heap is `O(n)`, we pop each max/min from it is `O(logn)` (to re-heapify the heap), so **heap is good at partial ordering!**

> Python functions for creating/using heap (priority queue) is [here](https://www.geeksforgeeks.org/heap-queue-or-heapq-in-python/).

#### Store a Heap

&nbsp;&nbsp;&nbsp;&nbsp;The array representation for heap is efficient, because binary heap is actually a **complete tree**. So, heap can be easily stored as array in **pre-order**. If the parent node is stored with index `i` then its left child has index `2*i+1` and its right child has index `2*i+2`, check [here](https://www.geeksforgeeks.org/heap-sort/).

&nbsp;&nbsp;&nbsp;&nbsp;Heap is a data structure good at **sorting/priority**. Heap is mainly used to represent a **priority queue** like [here](https://www.geeksforgeeks.org/heap-queue-or-heapq-in-python/). 

#### Build Max/Min Heap

&nbsp;&nbsp;&nbsp;&nbsp;The complexity for building a max/min heap is `O(nlogn)`, but by more detailed analysis **the real time complexity is `O(n)`**. See [here](https://www.cs.bgu.ac.il/~ds122/wiki.files/Presentation09.pdf) for more detail.

&nbsp;&nbsp;&nbsp;&nbsp;To check the complete process for building a max heap [here](https://www.youtube.com/watch?v=WsNQuCa_-PU&t=12s).

#### Push and Pop heap

&nbsp;&nbsp;&nbsp;&nbsp;According to [this solution](https://leetcode.com/problems/kth-largest-element-in-an-array/discuss/167837/Python-or-tm), even in the `heapq` module, heap is **represented with array/list**. The function `heapq.heapify(list)` is just doing heapify for the list. Then we just `heapq.heappop(list)` to pop the largest elements.

#### Heap Sort

> The video in [this tutorial](https://www.geeksforgeeks.org/heap-sort/) is a perfect illustration for heapsort.

&nbsp;&nbsp;&nbsp;&nbsp;The key for heap sort is that **the root of max heap is always the largest number**. So, in heap sort, they just **put the root to the end of array**, and after `n` times, the array will be sorted. The complexity for heapify edited array is `logn`, so the total complexity for heap sort is `nlogn`.

#### `heapq` Package

* In python's `heapq` package, `heapq.heapify()` defaults to be **min-heap**.
* `heapq.heapify(list)` **doesn't have return value!** It just heapify the input array.
* `heapq.heappop(list)` will directly pop the root (minimum) from that list.
* To push element to heap is `heapq.heappush(list, element)`.
* To heapify with **key** check [here](https://stackoverflow.com/questions/7803121/in-python-heapq-heapify-doesnt-take-cmp-or-key-functions-as-arguments-like-sor). To store a tuple to heap, the first element is priority and the second is the content.

### Stack

> Just like what we did in micro-controller, stack is very good at **store current result for future usage!** Take a look at [this problem](https://leetcode.com/problems/basic-calculator-ii/discuss/63076/Python-short-solution-with-stack.) and it will be clear.

&nbsp;&nbsp;&nbsp;&nbsp;According to the use of queue and stack in DFS/BFS, stack and queue is actually good for **sequential operation**. When you have decided/clear up the **sequential algorithm**, such as DFS or the above question.

