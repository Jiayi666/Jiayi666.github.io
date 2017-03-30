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
*	python3中不存在`xrange`函数了，其实python3中的`range`就是python2中的`xrange`，原本的`range`被删除了，见[这里](http://stackoverflow.com/questions/15014310/why-is-there-no-xrange-function-in-python3)。另外，`range(10)`产生的是从0到9共10个数。

### print
*	在python2中，`print`函数是不需要加括号使用的，可以直接`print x, y`，但是在python3中`print`函数必须使用括号。
*	上述`print(x, y)`默认会使用**空格**来隔开x与y参数。
*	`print`函数本质上是在调用输入对象的`__str__`方法，而且有上述的连续print规则，所以在python的print函数中进行计算只要最后有含有`__str__`方法的对象得到就可以了。
*	如果不想使用默认的空格分隔方法，可以用**string formatting**，如`hw12 = '%s %s %d' % (hello, world, 12)`。

### List
*	与R语言中不同，list是不能通过直接赋值增加元素的，例如`x=[]; x[0]=1`在python中不能成立，只能用`list.append()`。
*	python中主要的循环方法是`for .. in ..`语句，但如果想在循环的同时得到对应元素的index，可以使用`enumerate`函数：
<pre>
		animals = ['cat', 'dog', 'monkey']
		for idx, animal in enumerate(animals):
    		print '#%d: %s' % (idx + 1, animal)
		# Prints "#1: cat", "#2: dog", "#3: monkey", each on its own line
</pre>
*	**list comprehension**是针对**对list中的每个元素进行操作**这种情况设计的，而且一般与赋值操作一起进行。注意，list comprehension对x的操作**只能有一步**，如果需要更复杂的操作应该使用function或者lambda function，关于使用lambda function的效率问题，可以参考[这里](http://stackoverflow.com/questions/6076270/python-lambda-function-in-list-comprehensions)。
<pre>
		nums = [0, 1, 2, 3, 4]
		squares = [x ** 2 for x in nums]
		print squares   # Prints [0, 1, 4, 9, 16]
</pre>
*	`list.remove()`函数很有意思，是remove**元素**，而不是根据index来remove，如`x=[1,10,20]; x.remove(20)`。

### Dictionary
*	与list不同，dict可以采用直接对新key赋值来添加新的元素，如`x={}, x['name']='jiayi'`。
*	访问dict中的元素一般只能用key，还没见到用item来访问的。
*	在使用`dict.get()`函数时要注意**添加默认值**，就是`d.get('monkey', 'N/A')`中的'N/A'，这样在d中不存在'monkey'时才会返回'N/A'，否则返回空字符。
*	所谓的dict comprehension，与list comprehension差别不大，只是在赋值之前加入了**key**：
<pre>
		nums = [0, 1, 2, 3, 4]
		even_num_to_square = {x: x ** 2 for x in nums if x % 2 == 0}
		print even_num_to_square  # Prints "{0: 0, 2: 4, 4: 16}"
</pre>

### Set
*	set虽然有和dict一样的建立符号`{}`，但其中元素的操作与list类似，set中元素的添加与删除只能通过`set.add()`与`set.remove()`函数进行。
*	由于set是**无序**的，对set的循环往往需要得到其index，与list一样，其index也是通过`enumerate()`函数得到。
*	所谓unordered，是指set中储存的元素**不能通过index访问**，只能用`a in set`来进行判断或者`add` or `remove`。
*	set也有comprehension方法，与前面的大同小异。comprehension方法就是**新建了一个对象**，而这个对像是list，dict还是set完全由其新建时的**符号**如`[], {x:}, {}`决定。

### Class
*	在inner scope的namespace中对变量进行赋值时python优先选择**建立新name**，只有当该名字被标注为global时才会在对其赋值时直接选择对**全局**变量赋值：
<pre>
		x = 5
		def func()
			global x = 10
			# x = 10
</pre>

　　上式中只有采用`global`关键字标注才能给身为全局变量的x**赋值**，否则只能**建立新变量x**，而外界的x对于`func`函数内部只是**read only**。
*	与`gloabl`类似的还有`nonlocal`，不同于直接查询全局变量的global，nonlocal关键字表示从**外层（非全局）**的name scope中寻找该变量，global与nonlocal的不同可以参考[这里](http://blog.csdn.net/xijiaoda_liuhao/article/details/8788624)。