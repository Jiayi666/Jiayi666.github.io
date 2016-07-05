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
*	IPython has brilliant completion function, using `a.<Tab>` IPython will display all the possible completion (here are methods of object a refers to). Note that I didn't say "output" but "display", because using `<Tab>` is only for a hint, IPython won't interrupt your work.
*	**"Duck" typing**
	>" When I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck."  ---- James Whitcomb Riley

According to Riley's theory, what's matters isn't what is an object but how this object can be used. Code like this can be used to check if an object is iterable, if it is not, we can use function like `x = list(x)` to convert it to be one.
<pre>
    def isiterable(obj):
	    try:
		    iter(ogj)	
		    return True
		except TypeError: #not iterable
			return False
</pre>
*	Import a module will bring it's name space unless it is imported directlyl.
*	Although Python is pass-by-reference, functions like `list(x)` always creat **a new list**. So for statement `a is not list(a)`, the return is `True`.

## Scalar Types