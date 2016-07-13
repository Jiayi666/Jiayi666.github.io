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

*	Using a question mark (?) before or after a variable will display some general information about the object.
*	Using ?? will also show the function’s source code if possible.
*	Any file can be run as a Python program inside the environment of your IPython session
using the %run command.
<pre>
		%run ipython_script_test.py
</pre>
*	Code snippets can be pasted from the clipboard in many cases by pressing `Ctrl-ShiftV`. 
*	`%paste` takes whatever text is in the clipboard and executes it as a single block
in the shell.
*	With the `%cpaste` block, you have the freedom to paste as much code as you like before
executing it.
