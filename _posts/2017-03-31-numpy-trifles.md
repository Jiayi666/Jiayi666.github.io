---
layout:     post
title:      "Numpy Trifles"
subtitle:   "Just beginner"
date:       2017-03-31
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - Python
---

> Numpy是一个用于矩阵计算的python库，其底层使用C语言编写，在进行矩阵运算的速度上大大超过了python，但是由于需要在每一步操作中在C和python间来回切换，也损失了一部分时间，而像tensorflow等架构则通过graph的方式减少了这部分损耗。

### ndarray
*	可以用*array index*的方式对array进行slicing。
<pre>
		# a is a ndarray
		print a[[0, 1, 2], [0, 1, 0]]
		print np.array([a[0, 0], a[1, 1], a[2, 0]])
		# the above two methods are equivalent
</pre>

*	ndarray有着和R语言中类似的**boolean indexing**机制，使用`a > 2`的方式得到array a的boolean array从而使用`a[a > 2]`来进行选取。

### array math
*	特别注意，**array 不是 matrix！！！**，在numpy中对ndarray的基础四则运算都是**element-wise**的，也就是说`*`操作并非矩阵乘法而是每个元素对应相乘，具体可参考[这里](http://cs231n.github.io/python-numpy-tutorial/#numpy-math)。
*	为了计算**内积**，numpy使用**dot operation**，即点积（**矩阵积**）。点积运算可以从np库中找到函数，也可以直接调用nparray对象的点积方法。
<pre>
		import numpy as np
		
		x = np.array([[1,2],[3,4]])
		y = np.array([[5,6],[7,8]])

		v = np.array([9,10])
		w = np.array([11, 12])

		# Inner product of vectors; both produce 219
		print v.dot(w)
		print np.dot(v, w)

		# Matrix / vector product; both produce the rank 1 array [29 67]
		print x.dot(v)
		print np.dot(x, v)

		# Matrix / matrix product; both produce the rank 2 array
		# [[19 22]
		#  [43 50]]
		print x.dot(y)
		print np.dot(x, y)
</pre>

*	Numpy提供了很多对ndarray进行数学运算的函数，可以从[这里](https://docs.scipy.org/doc/numpy/reference/routines.math.html)查看所有内置的数学函数。其中很多函数自带了**对某个维度作用**的功能，值得一看。
<pre>
		import numpy as np

		x = np.array([[1,2],[3,4]])

		print np.sum(x)  # Compute sum of all elements; prints "10"
		print np.sum(x, axis=0)  # Compute sum of each column; prints "[4 6]"
		print np.sum(x, axis=1)  # Compute sum of each row; prints "[3 7]"
</pre>

*	除了数学计算，Numpy还提供了很多函数对ndarray进行*manipulate*，比如转置，改变维度等等，可以在[这里](https://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html)查阅。注意，对一维array的转置**没有做用**，只能通过`np.reshape()`方法将行向量改变成列向量。
<pre>
		import numpy as np

		x = np.array([[1,2], [3,4]])
		print x    # Prints "[[1 2]
 		          #          [3 4]]"
		print x.T  # Prints "[[1 3]
    		       #          [2 4]]"

		# Note that taking the transpose of a rank 1 array does nothing:
		v = np.array([1,2,3])
		print v    # Prints "[1 2 3]"
		print v.T  # Prints "[1 2 3]"
</pre>

### Broadcasting
*	Numpy有很神奇的Broadcasting规则。所谓broadcasting是指*在array维度不匹配的条件下进行计算的规则*，其主要规则如下：
<pre>
		1. If the arrays do not have the same rank, prepend the shape of the lower rank array with 1s until both shapes have the same length.
		2. The two arrays are said to be compatible in a dimension if they have the same size in the dimension, or if one of the arrays has size 1 in that dimension.
		3. The arrays can be broadcast together if they are compatible in all dimensions.
		4. After broadcasting, each array behaves as if it had shape equal to the elementwise maximum of shapes of the two input arrays.
		5. In any dimension where one array had size 1 and the other array had size greater than 1, the first array behaves as if it were copied along that dimension
</pre>

*	简单来说，就是扩展rank较小的array让进行操作的两个array相互**匹配**，需要注意的是这个扩展工作是**按维度进行的**。比如
<pre>
		# Compute outer product of vectors
		v = np.array([1,2,3])  # v has shape (3,)
		w = np.array([4,5])    # w has shape (2,)
		# To compute an outer product, we first reshape v to be a column
		# vector of shape (3, 1); we can then broadcast it against w to yield
		# an output of shape (3, 2), which is the outer product of v and w:
		# [[ 4  5]
		#  [ 8 10]
		#  [12 15]]
		print np.reshape(v, (3, 1)) * w
</pre>

上面`np.reshape(v, (3, 1)) * w`的时候ｖ的维度是(3,1)，ｗ的维度是(1,2)，所以ｖ需要**在axis=1扩展，而ｗ需要在axis=0扩展**。