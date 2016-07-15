---
layout:     post
title:      "IPython An Interactive Computing Environment"
subtitle:   "Python for data analysis - Chapter03"
date:       2016-07-15
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Python
---

## Introspection

*	Using a question mark `?` before or after a variable will display some general information about the object.
*	Using `??` will also show the function’s source code if possible.
*	Any file can be run as a Python program inside the environment of your IPython session
using the `%run` command.
<pre>
		%run ipython_script_test.py
</pre>
*	Code snippets can be pasted from the clipboard in many cases by pressing `Ctrl-ShiftV`. 
*	`%paste` takes whatever text is in the clipboard and executes it as a single block
in the shell.
*	With the `%cpaste` block, you have the freedom to paste as much code as you like before
executing it.
*	IPython keyboard shortcut, which is familiar to users of the Emacs text editor or the UNIX bash shell.

![img](\img\in-post\ipython-keyboard-shortcut.bmp)

*	Magic functions can be used by default **without the percent sign**, as long as no variable is defined with the same name as the magic function in question. This feature is called automagic and can be enabled or disabled using `%automagic`.
*	IPython’s documentation is easily accessible from within the system, I encourage you to explore all of the special commands available by typing %quickref or %magic. 

![img](\img\in-post\frequently-used magic commands.bmp)

*	There is several IDE mode for IPython, but in Win7, I use the IPython installed in Anaconda witch has the function of those IDEs.

## Using the command history

*	IPython stores **references to both the input (the text that you type) and output (the object that is returned) in special variables**. So after input line 27, say, there will be two new variables `_27` (for the output) and `_i27` for the input.
*	由于IPython自动储存input、output数据的特点，即是已经使用了`del`删除变量，IPython中依然会保留着响应变量的引用，所以在处理大批量数据时应注意`%xdel`与`%reset`释放内存空间。
*	If you want to save the code you've write in IPython interactive session, you can use the `%logstart` magic function to preserve all the code in the session and future code you write.

## Interacting with OS

*	In IPython, many magic functions can be used to imitate operations in system command lines.

![img](\img\in-post\ipython-OS.png)

*	Starting a line in IPython with an exclamation point !, or bang, tells IPython to execute everything after the bang in the system shell, see `!cmd`.
*	The console output of a shell command can be stored in a variable by assigning the !-escaped expression to a variable. For example, check the IP address:

<pre>
		In [1]: ip_info = !ifconfig eth0 | grep "inet "
		In [2]: ip_info[0].strip()
		Out[2]: 'inet addr:192.168.1.137 Bcast:192.168.1.255 Mask:255.255.255.0'
</pre>

*	Multiple commands can be executed just as on the command line by separating them with semicolons:

<pre>
		In [558]: %alias test_alias (cd ch08; ls; cd ..)
		In [559]: test_alias
		macrodata.csv spx.csv tips.csv
</pre>

*	IPython has a simple **directory bookmarking** system to enable you to save aliases for common directories so that you can jump around very easily. (**and the bookmark won't be deleted even if you shut off the session**)

<pre>
In [6]: %bookmark default /jiayiliu/ipython_default_directoryIn 
[7]: cd db
(bookmark:db) -> /jiayiliu/ipython_default_directoryIn 
/jiayiliu/ipython_default_directoryIn 
</pre>

## Software development tools

#### Interactive debuger

*	Using `%debug` command right after an exception is raised, will switch IPython into debug mode, where the input mark changes to `ipdb>`. Once inside the debugger, you can execute arbitrary Python code and **explore all of the objects and data (which have been “kept alive” by the interpreter) inside each stack frame (function call stack)**.

![img](\img\in-post\ipython-debug.png)

*	Executing the %pdb command makes it so that IPython automatically invokes the debugger after any exception, a mode that many users will find especially useful.
*	Note that **debugger commands take precedence over variable names**; in such cases preface the variables with `!` to examine their contents.
*	Setting `set_trace()` and `debug()` functions in IPython profile can save a lot of time. While `set_trace()` can set breakpoint when you are writing codes, `debug()` can check the function invoking. You can check the book "Python for data analysis" chapter 03 page 66 about how to set them.
*	Using `%run -d` can directly switch into debug mode when you want to execute a py file.

#### Timing Code

*	IPython has two magic functions %time and %timeit to automatically calculate the time for statement after them.
<pre>
		In [561]: %time method1 = [x for x in strings if x.startswith('foo')]
		CPU times: user 0.19 s, sys: 0.00 s, total: 0.19 s
		Wall time: 0.19 s

		In [563]: %timeit [x for x in strings if x.startswith('foo')]
		10 loops, best of 3: 159 ms per loop
</pre>

Compared with `%time`, `%timeit` provide automatically loop to test the best performance for that statement.

#### Profiling

*	When developing high performance calculating program, it's important to have a global view of **how much time was cost by each function**, here you need profiling.
*	In IPython, `%run -p` and `%prun` magic function are used to display the profiling:

<pre>
		In [572]: %prun add_and_sum(x, y)
				4 function calls in 0.049 seconds
			Ordered by: internal time
			ncalls tottime percall cumtime percall filename:lineno(function)
				1 0.036 0.036 0.046 0.046 prof_mod.py:3(add_and_sum)
				1 0.009 0.009 0.009 0.009 {method 'sum' of 'numpy.ndarray' objects}
				1 0.003 0.003 0.049 0.049 <string>:1(<module>)
				1 0.000 0.000 0.000 0.000 {method 'disable' of '_lsprof.Profiler' objects}
</pre>

*	However, as the upper code shows, it's inconvenient to analyse your code when all the functions agregated. So, IPython offers a **profiling by line** function `%lprun`.

<pre>
		In [573]: %lprun -f add_and_sum add_and_sum(x, y)
		Timer unit: 1e-06 s
		File: book_scripts/prof_mod.py
		Function: add_and_sum at line 3
		Total time: 0.045936 s
		Line # Hits Time Per Hit % Time Line Contents
		==============================================================
			3				def add_and_sum(x, y):
			4 	1 	36510	36510.0	79.5	added = x + y
			5 	1 	9425	9425.0 	20.5	summed = added.sum(axis=1)
			6 	1 	1	1.0	0.0	return summed
</pre>

*	We also can use `In [574]: %lprun -f add_and_sum -f call_function call_function()` like statement to run two functions at the same time.

#### Tips for Productive Code Development

*	Python has a **load once** module system, where in the same **session**, the same module will only be loaded once, even if you've made changes to that module.
*	For this problem, IPython has a special dreload function (not a magic function) for “deep” (recursive) reloading of modules. If I were to run `import some_lib` then type `dreload(some_lib)`, it will attempt to reload some_lib as well as all of its **dependencies**. This will not work in all cases, unfortunately, but when it does it beats having to restart IPython.

#### Make your own class IPython-friendly

*	In IPython, the built-in function `pprint` is designed to make elegent printing of basic data structures like tuple and list. But when it comes to your own class, it may won't work well 

<pre>
		class Message:
			def __init__(self, msg):
			self.msg = msg

		In [576]: x = Message('I have a secret')
		In [577]: x
		Out[577]: <__main__.Message instance at 0x60ebbd8>
</pre>

And the way to solve this is using the `__repr__` magic method and **print that to the concle**.

<pre>
		class Message:
			def __init__(self, msg):
			self.msg = msg

			def __repr__(self):
			return 'Message: %s' % self.msg

		In [579]: x = Message('I have a secret')
		In [580]: x
		Out[580]: Message: I have a secret
</pre>