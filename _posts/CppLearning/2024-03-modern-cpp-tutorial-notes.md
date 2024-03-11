---
layout:     post
title:      "Modern Cpp Tutorial C++11/14/17/20 On The Fly Notes"
subtitle:   ""
date:       2024-03-10
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - C++
---

## Modern Cpp Tutorial C++11/14/17/20 On The Fly

This is an open source book by Changkun Ou https://github.com/changkun/modern-cpp-tutorial which covers the new features introduced along C++11/14/17/20.

This book is very helpful for people from the legacy C/C++ world to get a quick scan on what's the new powerful tools available in modern C++ (up to C++20).

## Chapter 02 - Languiage usability enhancement

Languiage usability refers to the languiage behavior BEFORE runtime, which includes both the process of writing and compiling the code.

### Constants

* `nullptr` has a special type while `NULL` in C is mostly just defined as 0 (or `(void*)0`) in compilers. So `nullptr` is much more precise on its use case and should always be preferred
* `constexpr` refers to values can be determined at compile time
    * Most compiler can optimize `const` to treat it like `constexpr` but strictly speaking `const a = 10; int b[a];` is illegal (C++ specifically requires a `constexpr`)
    * For functions that returns `constexpr` it simply means the return value **CAN** be `constexpr` (if the parameters passed is also `constexpr`) such as returning Nth value in fibonachi arrays

### Variable Initialization

* `C++14` allows declaring variables in `if` and `switch` statement to avoid having to re-use/change loop variable names (eg. `if (auto itr = x.find(y); itr != x.end())`)
* In legacy C, PODs (Plain Old Data - class with no constructor, destructor, and virtual methods) and structs can be initialized with `{}` but to invoke customized constructor it needs a function call operator `()`
    * `C++11` introduced `std::initialization_list` type and allow creating constructor taking `std::initialization_list` which unified the above gap
    * Since `C++11` using `{}` can uniformly initialize any type
* `C++17` provided **Structured Binding** allows "multiple return values" like other languages


