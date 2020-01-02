---
layout:     post
title:      "C++ Containers"
subtitle:   ""
date:       2020-01-01
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - C++
    - Programming
---

- [C++ Containers](https://www.geeksforgeeks.org/containers-cpp-stl/)

### Unordered associative containers

##### Traversal with iterator

```
for (itr = umap.begin(); itr != umap.end(); itr++) 
    { 
        // itr works as a pointer to pair<string, double> 
        // type itr->first stores the key part  and 
        // itr->second stroes the value part 
        cout << itr->first << "  " << itr->second << endl; 
     } 
```

&nbsp;&nbsp;&nbsp;&nbsp;Iterator is **a pointer** to an element in the container. So, use `*iter` or `iter->member` to access the element or member of the element.

##### unordered_set (HashSet)

> Collection of unique keys, hashed by keys. (class template).

- Creation : `unordered_set<int> intSet;`
- Add : `intSet.insert(num);`
- Find : `intSet.find(num);` If not found, the critieria is `set.find(num) == set.end();`

##### unordered_map (HashMap)

> Collection of key-value pairs, hashed by keys, keys are unique. (class template).

- Creation : `unordered_map<string, int> wordFreq;`
- Add : `wordFreq[key] = 1;`
- Check key existance : `if(unmap.find(key) == unmap.end())`

### Vector

> According to [this tutorial](https://www.geeksforgeeks.org/vector-in-cpp-stl/).

- Creation : `vector<int> vec;`
- Add : `vec.push_back(num);`
- Get : `vec[ind]` or `vec.at(ind)`
- Remove : `vec.erase(ind)`
- size
- empty
- insert : `vec.insert(ind, val)`

### Container adaptors

> Container adaptors provide a different interface for sequential containers.

##### stack

- empty : returns whether the stack is empty
- size : the same as all other sequential containers
- top : return the top element (next to be pushed)
- push
- pop

##### queue

- empty
- size
- push
- pop
- front : returns a reference to the first element of the queue.
- back : returns a reference to the last element of the queue.

##### priority_queue

> The first element of the priority_queue is the greatest of all elements in the queue and **elements are in non-increasing order**.

### make_heap

> According to [this tutorial](https://en.cppreference.com/w/cpp/algorithm/make_heap), we can use `std::make_heap` to create a heap.

&nbsp;&nbsp;&nbsp;&nbsp;**Vector** to **Max** heap :

- Creation : `std::make_heap(v.begin(), v.end());`
- pop : `std::pop_heap(v.begin(), v.end());`
- push : **directly push to vector** then run `std::push_heap(v.begin(), v.end());` to heapify it.