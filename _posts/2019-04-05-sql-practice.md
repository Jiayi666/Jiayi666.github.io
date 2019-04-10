---
layout:     post
title:      "SQL Practice"
subtitle:   "Deeper SQL"
date:       2019-04-05
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Database
    - SQL
---

> The first website I did SQL practice is in [hacker rank](https://www.hackerrank.com/domains/sql?filters%5Bstatus%5D%5B%5D=unsolved&badge_type=sql).

> Window functions only available after MYSQL 8.0.

### Table Manipulation

### Variable Manipulation

#### Extract existing variables

#### From current variables to New variables

> Check [this tutorial](https://www.w3schools.com/SQl/sql_ref_mysql.asp) for all the MySQL functions for string, number and dates.

> There are direct and undirect operations for variables. Direct operations as `+-*/`, indirect operations as **conditional operation**.

##### String direct operations

- `length(Var)` return the length of the string variable, remember it's different from python `len`.
- `substring(Var,start,end)` to get the substring from a `varchar` or `char` variable. The difference between `varchar(n)` and `char(n)` is varchar can any length under `n` while char can only be length `n`.
- `left(string,len)` and `right(string,len)`.

##### Case operation

> It needs extra care that `case` operation shouldn't have **overlaping** between its critierion!

&nbsp;&nbsp;&nbsp;&nbsp;According to [here](https://www.w3schools.com/SQl/sql_case.asp).

> The CASE statement goes through conditions and returns a value when **the first condition is met** (like an IF-THEN-ELSE statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.