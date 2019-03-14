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

### Hashing

#### Hash Table

&nbsp;&nbsp;&nbsp;&nbsp;As in [this problem](https://leetcode.com/problems/copy-list-with-random-pointer/discuss/43485/Clear-and-short-python-O(2n)-and-O(n)-solution), hash table is actually building a **one-to-one mapping** between any two space! The key can be any object, so does the values.

#### Hash Set

&nbsp;&nbsp;&nbsp;&nbsp;Hash set in python is just `set(xxx)`. Unlike hash table, hash set doesn't care what is the value for each key, it just care **if an element exists in the set**.

#### The procedure of hash table/map

&nbsp;&nbsp;&nbsp;&nbsp;For insertion of a key(K) – value(V) pair into a hash map, 3 steps are required:

1. K is converted into a small integer (called its hash code) using a **hash function**.
2. The hash code is used to find an **index** (hashCode % arrSize) and the entire linked list at that index(Separate chaining) is first searched for the presence of the K already.
3. If found, it’s value is updated and if not, the K-V pair is stored as a new node in the list.

#### Collision Handling

&nbsp;&nbsp;&nbsp;&nbsp;Since a hash function gets us a small number for a big key, there is possibility that two keys result in same value. The situation where a newly inserted key maps to an already occupied slot in hash table is called collision.

&nbsp;&nbsp;&nbsp;&nbsp;There are two major ways to handle collisions in hashing.

* Seperate Chaining (Use liked list to stored elements in collision)
* Open Addressing (Store the collision in next empty space)

#### Rehashing

&nbsp;&nbsp;&nbsp;&nbsp;Rehashing happens when the **load factor** (defined as `n/b` where `n` is the number of entries and `b` is the size of matrix/array). By default, when load factor is greater than 0.75, we will do rehashing to **ensure the performance**.

&nbsp;&nbsp;&nbsp;&nbsp;In rehashing, we **double** the size of the matrix. We just make a new matrix and **insert** the previous elements to the new matrix.

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

### Tree

#### BST

> The smallest item in a BST is always the left most child, the largest item in as BST is always the right most child.

##### Construction of BST

&nbsp;&nbsp;&nbsp;&nbsp;There are two kind of tasks when building a BST.

1. Reconstruct a BST that is transformed to an array.
2. Build a *balanced* BST from an array.

&nbsp;&nbsp;&nbsp;&nbsp;The first task can be done by having **preorder traversal** of the origin BST.

&nbsp;&nbsp;&nbsp;&nbsp;The second task can be done by finding the **middle value** for the sorted array and recursively do to the right and left children.

##### Deletion of BST

&nbsp;&nbsp;&nbsp;&nbsp;One great property for BST is it has quick insertion and deletion speed compared with other sorted data structures.

&nbsp;&nbsp;&nbsp;&nbsp;There are three situations that we may encounter when deleting elements from BST:

1. Deleting a node with no children: simply remove the node from the tree.
2. Deleting a node with one child: remove the node and replace it with its child.
3. Deleting a node with **two children**: call the node to be deleted D. 

&nbsp;&nbsp;&nbsp;&nbsp;The third situation is the most complicated, check [here](https://en.wikipedia.org/wiki/Binary_search_tree#Deletion) for more detail.

#### Trie

> The name 'Trie' is from 're**trie**val' and read as 'try'.

> The advantage of trie only appears when we try to storea and **match** sequential object and there is a limited choice of each element in each position, such as string.

&nbsp;&nbsp;&nbsp;&nbsp;According to [this tutorial](https://www.geeksforgeeks.org/trie-insert-and-search/), trie can reduce the time complexity for **matching** string in BST from `O(M*logN)`, where `M` is the length of the string to be matched and `N` is the number of elements in the BST, to `O(M)`.

&nbsp;&nbsp;&nbsp;&nbsp;The space complexity for trie only related with the length of the key (the length of the string to be matched) and the number of keys being stored. The branching factor is determined to the the length of the alphabet, it is 26.

&nbsp;&nbsp;&nbsp;&nbsp;Check [this tutorial](https://www.geeksforgeeks.org/trie-insert-and-search/) for the insertion and search, [this tutorial](https://www.geeksforgeeks.org/trie-delete/) for deletion in trie.

