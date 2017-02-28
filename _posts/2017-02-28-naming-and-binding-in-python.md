---
layout:     post
title:      "Name, object and bind in python"
subtitle:   "Object Oriented Programming"
date:       2017-02-28
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - Python
---

### Object in Python
*	python中的**所有data**都是object。
*	什么是所谓的data？任何程序运行中需要在内存中储存的数据都是data。程序运行的code是data，用户定义的一个class type是data，`x=[1,2,3]`中用户**输入**的list也是data。
*	在python中，一旦一个object被创建，其就拥有了唯一的id，直到这个object不再与任何name相联系时这个id才失效（内存被释放）。这个id在CPython中直接使用了储存该object的地址指针。
*	除此之外，每个object都有其对应的type和value。其中**type决定了该object中数据被储存的方式和能对数据进行的操作**；value则是储存在其中的数据本身。

### Naming and Binding
##### Passing by value / reference
　　对函数进行调用时输入的实参有**pass by value**和**pass by reference**两种情况，其中by value的方法会**创建**一组实参的复制，并将复制的object与虚参相连。而by reference的方法则类似于传递指针，可以允许通过虚参改变实参的内容，相比于by value，pass by reference的方法由于不用创建新的object，效率更高。

　　python语言中的参数传递不同于上述两种，但更偏向passing by reference，在此就暂时叫它[passing by name](http://stackoverflow.com/questions/41883406/is-python-function-passing-by-reference)吧。前面的链接给出了stackoverflow上关于python参数传递的一个讨论，下面我们先看看python中name与object之间binding的问题。

　　[官方文档](https://docs.python.org/3/reference/executionmodel.html#naming-and-binding)给出了部分对naming and binding的解释，并且[这里](https://nedbatchelder.com/text/names.html)对python中name与value/object之间的关系讲的非常透彻，非常推荐读上面第二个网站，并可以在其中给出的[python分析网站](http://pythontutor.com/)中自己体验一下。简单来说，python中不存在类似C++中的pointer或reference，python中变量名(name)与object间的关系就是“bind”，而将name与object相联系的操作就是**赋值**。

　　python的赋值操作**不会建立任何新object**，例如`x=x+1`中如果x是number类型，语句中建立新object的操作是`x+1`，而赋值仅仅是将该object与名字x进行关联。

　　所以说，python中对虚参的赋值就是将实参对应的object与虚参名字之间建立关联，类似于pass by reference。这里解释一下开头stackoverflow中关于参数传递的疑问，为什么：
<pre>
def append_element(some_list, element):
    some_list.append(element)

data = [3, 1, 2]
append_element(data, 4)

print(data)
[3,1,2,4]
</pre>
　　上面python对于参数的传递表现的像pass by reference，可以通过虚参改变实参object的内容。但是对于下面的情况：
<pre>
def test(x):
	return(x=x+1)
b = test(a)
print(a ,b)
1 2
</pre>
　　上面的代码中虚参又无法改变实参，类似于pass by value。

　　其实出现上述疑问的关键还是在于python的OOP(Object Oriented Programming)特性。python非常严格地将所有数据都作为一个个object，而在函数内对虚参的操作，本质上来说**还是对object的操作**。由于每个object都对应了一定的type，而type规定了object所能进行的操作。python中的type有两种，mutable和immutable。其中number，string，tuple等属于immutable；list，dictionary等属于mutable。

　　上面的例子中，第一段代码中实参是list，是mutable的数据，所以通过虚参的name可以直接对实参的object进行修改。但是第二段中实参是number，是immutable的数据，所以在运行`x=x+1`时**建立了新的object**，所以此时被赋值的x指向新建的object，而非实参的object，而实参的object并未改变。所以，不同于pass by value和pass by reference，python中的数据传递只是建立了虚参name与实参object的bind，而实际的操作，完全由object的类型决定。