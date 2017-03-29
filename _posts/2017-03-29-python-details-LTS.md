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

### print
*	在python2中，`print`函数是不需要加括号使用的，可以直接`print x, y`，但是在python3中`print`函数必须使用括号。
*	上述`print(x, y)`默认会使用**空格**来隔开x与y参数。
*	`print`函数本质上是在调用输入对象的`__str__`方法，而且有上述的连续print规则，所以在python的print函数中进行计算只要最后有含有`__str__`方法的对象得到就可以了。
*	如果不想使用默认的空格分隔方法，可以用**string formatting**，如`hw12 = '%s %s %d' % (hello, world, 12)`。

### List
*	与R语言中不同，list是不能通过直接赋值增加元素的，例如`x=[]; x[0]=1`在python中不能成立，只能用`list.append()`。
*	

