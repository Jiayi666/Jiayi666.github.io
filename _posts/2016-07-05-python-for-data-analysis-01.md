---
layout:     post
title:      "Python Language Essentials"
subtitle:   "Python for data analysis - Appendix"
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
> " When I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck."  ---- James Whitcomb Riley

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

#### Numerical Types

*	The size of interger can be sorted as **int** is dependent on operation system (32bits/64bits)
*	Python will automatically convert a very large interger into **long** type, which can store arbitrarily large intergers.
*	In python3, interger division not resulting in a whole number will yield a floating point number, but in python27, things are different, unless you put `from __future__ import division` at the begining of your module.
*	In python a string object with backslash '\' is different with print(), which will treat backslash as escape mark.
*	**templating and formatting string** can use the `%` mark
<pre>
		In [1]: template = '%.2f %s are worth $%d'
		In [2]: template % (4.5560, 'Argentine Pesos', 1)
		Out[2]: '4.56 Argentine Pesos are worth $1'
</pre>
*	Boolean values are combined with the **and** and **or** keywords.
*	The build-in Python module `datetime` provides `datetime`, `date`, and `time` type, and **each type can have an instantiation**.

#### Exception Handling

*	Using exception handling method, we can **supress typical exceptions and do something no matter exceptions raised or not**.

<pre>
		f = open(path, 'w')
		
		try:
		  write_to_file(f)
		except (TypeError, ValueError):
		  print 'Failed'
		else:
		  print 'succeeded'
		finally:
		  f.close()
</pre>

#### range and xrange

*	range(start, end, step) will produce a list (in Python3, range also produce an iterator, no need for xrange)
*	xrange(start, end, step) will produce an iterator

#### Ternary Expressions

*	a ternary expression combines an if-else block to a single line.

<pre>
		value = true-expr if condition else false-expr
</pre>

## Data Structures and Sequences

### Tuple

*	The size and content of tuples cannot be modified, they can only be changed by instamce methods.
*	Easy way to build tuples:
<pre> 
		In [2]: 1, 2
		Out[2]: (1, 2)
</pre>

*	Tuples can be contatenated using the + operator
<pre>
		In [2]: (4, None, 'foo') + (6, 0) + ('bar',)
		Out[2]: (4, None, 'foo', 6, 0, 'bar')
</pre>

*	Unpacking Tuples (see "Easy way to build tuples")
<pre>
		seq = [(1, 2, 3), (4, 5, 6)]
		for a, b, c in seq:
			pass
</pre>

### List

*	Lists and tuples are semantically similar as one-dimensional sequences of objects and thus can be used interchangeably in many functions.
*	In python, the start of a sequence is marked with 0, such as list[0].
*	Lists can be concatenated by using + operator and .extend or .append methods. Note that using + operator is manipulated two objects at the same time, and a new list must be build, which is a very expensive operation. Thus, using extend to append elements to an existing list is usually preferable.
<pre>
		everything = []
		for chunk in list_of_lists:
			everything.extend(chunk)
</pre>

**here I need Figure A-2 in page 411**

### Built-in Sequence Functions

*	These functions **aren't methods** for certen data structures, they are useable for all sequences in Python, they used like **enumerate(list/tuple/string)**.
*	**enumerate** will help you keep track of the index of the current item during iteration.
*	**sorted** returns a new sorted **list** from the elements of any sequences.
*	**zip** pairs up the elements of a number of lists, tuples or sequences to create a list of tuples.
<pre>
		In [1]: seq1 = ('baz', 'bar', 'foo')
		In [2]: seq2 = (1, 2, 3)
		In [3]: zip(seq1, seq2)
		Out[3]: [('baz', 1), ('bar', 2), ('foo', 3)]
</pre>

