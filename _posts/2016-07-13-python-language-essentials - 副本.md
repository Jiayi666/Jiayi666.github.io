---
layout:     post
title:      "test"
subtitle:   "Python for data analysis - Appendix"
date:       2016-07-15
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

#### Tuple

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

#### List

*	Lists and tuples are semantically similar as one-dimensional sequences of objects and thus can be used interchangeably in many functions.
*	In python, the start of a sequence is marked with 0, such as list[0].
*	Lists can be concatenated by using + operator and .extend or .append methods. Note that using + operator is manipulated two objects at the same time, and a new list must be build, which is a very expensive operation. Thus, using extend to append elements to an existing list is usually preferable.
<pre>
		everything = []
		for chunk in list_of_lists:
			everything.extend(chunk)
</pre>
*	In python, sequences as list and tuple can be sliced using the index operator `[]`. Keep an eye on the negative index.

![img](/img/in-post/Python-slice.bmp)

*	A **step** can also be used after a second colon to **take every other element**:
<pre>
		In [2]: seq = [7, 2, 3, 7, 5, 6, 0, 1]
		In [3]: seq[::2]
		Out[3]: [7, 3, 3, 6, 1]
</pre>
In the upper example, `seq[::2]` will **choose every two index start from 0**.
<pre>
		In [2]: seq = [7, 2, 3, 7, 5, 6, 0, 1]
		In [3]: seq[::-1]
		Out[3]: [1, 0, 6, 5, 7, 3, 2, 7]
</pre>
This is an easy way to reverse a list or a tuple.

#### Built-in Sequence Functions

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
*	**reversed** itrates over the elements of a sequence in reversed order (**`reversed()`returns an iterator**)
<pre>
		In [2]: reversed(range(10))
		Out[2]: < listreverseiterator at 0x3988390>
		In [3]: list(reversed(range(10)))
		Out[3]: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
</pre>

#### Dict

> Dict is essentially a collection of 2-tuples.

*	Using `dict[key] =` syntax as access to insert or set elements in a dict.
*	You can check if a key is using in a dict using `'key' in dict` which is similar to check if a value is in a list or tuple `value in list/tuple`
*	Merge two dict use `dict.update(another_dict)` method.
*	Build a dict using two lists/tuples: `dict1 = dict(zip(range(5), reversed(range(5))))` 
*	Using `dict.pop(key)` to delete elements in a dict, or you can use `del dict[key]` to do the same thing.

#### Set

*	Set can be build using **dict only keys** and `set()` function.
*	Sets in python can do all the set-related mathematical operations `| & ^` etc.
*	Set have `issubset(), issuperset(), isdisjoint()` methods. And all the set operations can be accomplished by using methods like `a.union(b)`.

#### List, set, and Dict Comprehensions

*	List comprehension
> *List comprehensions* are one of the most loved Python-language features. They allow you to concisely **form a new list** by filtering the elements of a collection and trnsforming the elements passing the filter in on conscise expression.

They have the basic form:

		`[exor for val in collection if condition]`

**keep an eye on the square brace which stand for list (output).**
<pre>
		In [2]: strings = ['a', 'bat', 'bb', 'cat']
		In [3]: [x.upper() for x in strings if len(x) > 2]
		Out[3]: ['BAT', 'CAT']
</pre>
*	Dict and Set comprehension

		`{key-expr : val-expr for val in collection if condition}`	
		`{expr for val in collection if condition}`

In dict and set comprehension, the square braces has been changed with curly braces, and dict comprehension need two expressions.
<pre>
		In [2]: strings = ['a', 'bat', 'bb', 'cat']
		In [3]: loc_mapping = {val : index for index, val in enumerate(strings)}
		In [4]: loc_mapping
		Out[4]: {'a':0, 'bat':1, 'bb':2, 'cat':3}
</pre>

## Functions

#### Functions are objects

Since functions are objects, you can **use functions as arguments to other functions**.

<pre>
		clean_ops = [str.strip, str.title]
		
		def clean_strings(strings, ops):
			result = []
			for value in strings:
				for function in ops:
					value = function(value)
				result.append(value)
			return result
</pre>

#### Anonymous (lambda) functions

Lambda functions are created using keyword `lambda` and **a single statement**, it has the basic form:

		`lambda [variable list] : expression`

The following two ways of defining functions are equal.
<pre>
		def short_fuctions(x, y)
			return x+y

		short_functions = lambda x, y: x+y
</pre>

#### Closures (闭包): Functions that return Functions

The key property of closure is that thet returned function still has access to the variables in the local namespace where it was created. 

In practice, we can use this attribute to keep track of what we have done before or use closure as a general mode to formating more specific functions. 

#### Extended Call Syntax with *args, **kwargs

When you write `func(a, b, c, d=some, e=value)`, the positional and keyword arguments are actually packed up into a tuple and dict, respectively **(positional → tuple; keyword → dict)**. So the internal function receives a tuple `args` and a dict `kwargs` and internally does the equivalent of:
<pre>
		a, b, c = args
		d = kwargs.get('d', d_default_value)
		e = kwargs.get('e', e_default_value)
</pre>

#### Currying: Partial Argument Application

<pre>	
		def add_numbers(x, y):
			return x+y

		add_five = lambda y: add_number(y, 5)
</pre>

#### Generators

A generator is a easy way to construct a iterable object. While normal functions execute and return a single value, generators return a sequence of value **lazily**. To creat a generator, use the `yield` keyword instead of `return` in a function (note that `yield` should be used **within** the `for` loop).

<pre>
		def squares(n=10)
			for i in xrange(1, n+1)
				print 'Generating squares from 1 to %d' % (n**2)
				yield i**2

		In [1]: gen = squares()

		In [2]: gen
		Out[2]: < generator object squares at 0x34c8280>

		In [3]: for x in gen:
					print x
		Out[3]: Generating squares from 1 to 10
				1 4 9 16 25 36 49 64 81 100
</pre>

As the upper example shows, what has been yield from the `squares()` function is a iterator containing all the numbers produced **after the `yield` keyword** (within the for loop). 

Generator 与 return 的区别在于`yield`不会打断程序的运行，但还是**每次运行到`yield`的时候才会产生iterator中的一个元素**.