---
layout:     post
title:      "Python基础细节"
subtitle:   "Long Time Support"
date:       2017-03-29
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - Python
---

### Language
*	python中没有定义'NA'，而是用'N/A'来表示数据不存在。

### print
*	在python2中，`print`函数是不需要加括号使用的，可以直接`print x, y`，但是在python3中`print`函数必须使用括号。
*	上述`print(x, y)`默认会使用**空格**来隔开x与y参数。
*	`print`函数本质上是在调用输入对象的`__str__`方法，而且有上述的连续print规则，所以在python的print函数中进行计算只要最后有含有`__str__`方法的对象得到就可以了。
*	如果不想使用默认的空格分隔方法，可以用**string formatting**，如`hw12 = '%s %s %d' % (hello, world, 12)`。

### List
*	与R语言中不同，list是不能通过直接赋值增加元素的，例如`x=[]; x[0]=1`在python中不能成立，只能用`list.append()`。
*	python中主要的循环方法是`for .. in ..`语句，但如果想在循环的同时得到对应元素的index，可以使用`enumerate`函数：
<pre/>
		animals = ['cat', 'dog', 'monkey']
		for idx, animal in enumerate(animals):
    		print '#%d: %s' % (idx + 1, animal)
		# Prints "#1: cat", "#2: dog", "#3: monkey", each on its own line
</pre>
*	**list comprehension**是针对**对list中的每个元素进行操作**这种情况设计的，而且一般与赋值操作一起进行。注意，list comprehension对x的操作**只能有一步**，如果需要更复杂的操作应该使用function或者lambda function，关于使用lambda function的效率问题，可以参考[这里](http://stackoverflow.com/questions/6076270/python-lambda-function-in-list-comprehensions)。
<pre/>
		nums = [0, 1, 2, 3, 4]
		squares = [x ** 2 for x in nums]
		print squares   # Prints [0, 1, 4, 9, 16]
</pre>

### Dictionary
*	与list不同，dict可以采用直接对新key赋值来添加新的元素，如`x={}, x['name']='jiayi'`。
*	访问dict中的元素一般只能用key，还没见到用item来访问的。
*	在使用`dict.get()`函数时要注意**添加默认值**，就是`d.get('monkey', 'N/A')`中的'N/A'，这样在d中不存在'monkey'时才会返回'N/A'，否则返回空字符。
*	所谓的dict comprehension，与list comprehension差别不大，只是在赋值之前加入了**key**：
<pre/>
		nums = [0, 1, 2, 3, 4]
		even_num_to_square = {x: x ** 2 for x in nums if x % 2 == 0}
		print even_num_to_square  # Prints "{0: 0, 2: 4, 4: 16}"
</pre>
