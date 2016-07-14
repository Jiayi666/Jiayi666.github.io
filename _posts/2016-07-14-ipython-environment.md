---
layout:     post
title:      "IPython An Interactive Computing Environment"
subtitle:   "Python for data analysis - Chapter03"
date:       2016-07-14
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