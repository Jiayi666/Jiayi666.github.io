---
layout:     post
title:      "Python for data analysis 01"
subtitle:   "Python basics & Scientific purpose"
date:       2016-07-05
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Python
---

> Knowledge is a treasure, but practice is the key to it. ----Thomas Fuller

## Language Semantics

*	Indentation + Colon, not braces
*	Use 4 spaces as default indentation
*	Python do not need to be terminated by semicolons
*	**Everything is an object**, which means we should treat everything in Python as a black box and just use the port it offeres.
*	**Pass by reference!** When assign a variable with another variable, they will be different references to the same object.
	<pre>
	   In[1]: a = [1,2,3]  
	   In[2]: b = a  
	   In[3]: a.append(4)  
	   In[4]: b  
	   Out[4]: [1, 2, 3, 4]  
	</pre>
As related concepts, pass-by-value and pass-by-reference are always talked togather, so it is very important for programmer to understand the difference between those two terms. Pass-by-value will **cause the duplication of an object** while pass-by-reference will only **add a new reference to an existed object**. 
*	There is no `type` attribute for references / variable names in Python. However python has been considered as a strong type programming language, because it's strict type-converting rules.We can use `isinstance()` function to check the type of a variable.