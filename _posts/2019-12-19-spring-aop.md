---
layout:     post
title:      "Aspect Oriented Programming"
subtitle:   "Spring with AspectJ"
date:       2019-12-19
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Java
    - Spring
---

##### Resources

- [Intro to AOP](https://www.baeldung.com/spring-aop)
- [Spring AOP Reference & Tutorial](https://howtodoinjava.com/spring-aop-tutorial/)

### Basic Idea of AOP

![img](\img\in-post\AOP\AOP_Intro.jpg)

&nbsp;&nbsp;&nbsp;&nbsp;As shown in the above graph, the idea of AOP (Aspect Oriented Programming) 
is to **cut** the program running with **aspects**. The most import terms in AOP can be easily 
understood with this paradigm. Check [this tutorial](https://www.baeldung.com/spring-aop) which gives
great introduction of the overall AOP idea.

### Important Concept

- **Aspect** is the action taken by an aspect at a particular join-point.
- **Joinpoint** is a point of execution of the program, such as the execution of a method or the handling of an exception. In Spring AOP, a joinpoint always represents a method execution.
- **Pointcut** is a predicate or expression that matches join points.
- **Advice** is associated with a pointcut expression and runs at any join point matched by the pointcut.

&nbsp;&nbsp;&nbsp;&nbsp;Using the below graph as a reference of each part in Spring AOP. Check [this tutorial](https://howtodoinjava.com/spring-aop-tutorial/) for more details.

![img](\img\in-post\AOP\spring-aop-diagram.jpg)

### Compiling with AOP

&nbsp;&nbsp;&nbsp;&nbsp;To add (**weave**) aspects into program that getting cut needs extra care. 
The simplest approach of weaving is compile-time weaving. When we have both the source code of the 
aspect and the code that we are using aspects in, the AspectJ compiler will compile from source and 
produce a woven class files as output. Afterward, upon execution of your code, the weaving process 
output class is loaded into JVM as a normal Java class. Check [this tutorial](https://www.baeldung.com/aspectj) for more information.
