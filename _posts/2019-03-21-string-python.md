---
layout:     post
title:      "Encoding and Decoding in Python"
subtitle:   "Deal with encoding / decoding error once and for all!"
date:       2019-03-21
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Python
---

> [This tutorial](https://nedbatchelder.com/text/unipain.html) is great for understanding basic principles for text storing and representing. Also, great handbook for encoding / decoding problems in python! Must take a look!

### What is **Unicode** and why?

> The existance of unicode gives enough space to *represent all human's symbols/languages*.

&nbsp;&nbsp;&nbsp;&nbsp;The main reason for us to use unicode instead of just ascii is that ascii can only represent 128 symbols, which is too less for human's languages.

### What's the problem in python?

#### Python 2

> Python 2 has an **implicite encoding/decoding** process, check the tutorial at the starting of this post for more detail.

&nbsp;&nbsp;&nbsp;&nbsp;It is truly confusing: we ask to encode a byte string to UTF-8, and get an error about not being about to decode as ASCII! The problem here is that byte strings can’t be encoded: remember encode is how you turn unicode into bytes. So to perform the encoding you want, Python 2 **needs a unicode string**, which it tries to get by implicitly decoding your bytes as ASCII.

#### Python 3

> In python 3, there are two kind of strings: <class str> and <class byte>. The "str" class is **unicode** and the byte class is encoded byte string.

&nbsp;&nbsp;&nbsp;&nbsp;In python 3, the “str” type that you get from a plain string literal stores unicode, and the “bytes” types stores bytes. You can create a bytes literal with a b prefix.

&nbsp;&nbsp;&nbsp;&nbsp;So “str” in Python 2 is now called “bytes,” and “unicode” in Python 2 is now called “str”. This makes more sense than the Python 2 names, since Unicode is how you want all text stored, and byte strings are only for when you are dealing with bytes.

