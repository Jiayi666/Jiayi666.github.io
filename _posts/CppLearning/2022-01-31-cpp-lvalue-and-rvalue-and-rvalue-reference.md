---
layout:     post
title:      "lvalue and rvalue In C++11"
subtitle:   "C++ Universal Reference"
date:       2022-01-31
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - C++
---

### lvalue and rvalue in C++

With C++11 and the introducing of "move" semantic, it is important to understand rvalue and "rvalue reference", which is a necessaty for C++ move semantics.

#### Reference

* [This rvalue reference tutorial](http://thbecker.net/articles/rvalue_references/section_01.html) from Thomas Becker explained well on what is rvalue, why we need rvalue reference, and how it is used to implement the move semantic.
* [This tutorial for "Universal Reference"](https://isocpp.org/blog/2012/11/universal-references-in-c11-scott-meyers) with Scott Meyers goes deeper on `&&` and why it can be used as an universal reference for both rvalue and lvalue.

#### What is lvalue and rvalue

##### Original Definition
An lvalue is an expression `e` that may appear on the left **or** on the right hand side of an assignment, whereas an rvalue is an expression that can **only** appear on the right hand side of an assignment.

##### A More Useful Definition
An lvalue is an expression that refers to a memory location and allows us to take the address of that memory location via the `&` operator. An rvalue is an expression that is not an lvalue.

#### Why Do We Need rvalue Reference
The most important use case for rvalue reference is to implement "move" semantics. The original assign or copy constructor takes a lvalue reference as input and will copy all underlying resource.

In order to **overload the old assign/copy constructor** and allow a direct "swap" of underlying resource without copy all of them, we introduced a new input type so we can explicitly favor the "swap/move" constructor.

* Assign constructor with lvalue reference: `X& X::operator=(X const & rhs)`
* Assign constructor with rvalue reference: `X& X::operator=(X&& rhs)` so when a rvalue reference is passed, it will only invoke this constructor.

It is possible that a class has only implemented the "move" constructor then when programmer tries to copy the object without move, it will be a compiling error.

##### How To Get rvalue Reference 
C++11 introduced `std::move` just to transform a lvalue to rvalue. It is basically recommended to use `std::move` whenever you can.

