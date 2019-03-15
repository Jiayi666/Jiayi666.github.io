---
layout:     post
title:      "How to solve algorithm designing problems?"
subtitle:   "Trade-offs between different data structure"
date:       2019-03-14
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Algorithm
    - Data Science
    - Problem Solving
---

## Fundamental Functions for Data Structures

&nbsp;&nbsp;&nbsp;&nbsp;In this section, I want to summarize the most commomly used **method abstractions** we will consider for **data manipulation**, such as create, insert, search etc.

### Create & Insert

&nbsp;&nbsp;&nbsp;&nbsp;I put create and insert togather is because in many situation the creation of a data structure is by inserting new items to the container. Such as array, linked list and many other containers.

### Retrival & Searching & Deletion

#### Sequentially Retrival

&nbsp;&nbsp;&nbsp;&nbsp;Queue, Stack, and Array, Linked List

#### Key-Value Pair Retrival 

> **Index** can be treated as a kind of key.

&nbsp;&nbsp;&nbsp;&nbsp;Hash table

#### Search for Existance

&nbsp;&nbsp;&nbsp;&nbsp;Hash Set has complexity `O(1)` to **search** if an element exist or not.

#### Search with Value

&nbsp;&nbsp;&nbsp;&nbsp;BST

### Sorting

#### Partially Sort

&nbsp;&nbsp;&nbsp;&nbsp;Heap

#### Sort with Insertion

&nbsp;&nbsp;&nbsp;&nbsp;BST

## Pros & Cons for Common Data Structures

### Hash Table/Set

##### Pros

1. Good for key-value pair search with `O(1)`.
2. Constant time insertion and deletion.

##### Cons

1. Can't do sorting at all.

### Linked List

> Give extra care for the **quick deletion** advantages for linked list, especially when the total size of memory is determined. For an array, we need to *move the whole array* after deletion! Linked list is very good at *deleting the end element* (maybe in reversed order storing).

##### Pros

1. Quick insertion & **deletion**, remember that the insertion for linked list is at **head**!
2. Sequencial property is preserved.

##### Cons

1. Hard to search/retrive specific element `O(N)`.
2. Won't work well along for sorting.

##### Target Works

1. Need both quick deletion and sequential property.

### BST

> Of course only work when we need a sorted data, otherwise hash table is much better.

##### Pros

1. Kept a sorted data structure.
2. Have insertion, deletion, searching complexity `O(logN)`.

##### Target Works

1. Sorted data with frequent insertion and deletion.
