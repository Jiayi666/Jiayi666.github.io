---
layout:     post
title:      "Java Chat Room"
subtitle:   "Multithread server and client"
date:       2019-07-03
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Java
    - Server
---

> Here is two major reference for this project: [DomHeal](https://github.com/DomHeal/JavaFX-Chat) and [Laity000](https://github.com/Laity000/ChatRoom-JavaFX). Laity000's project also has his design process of his chatroom which helps a lot.

### Communication

#### What Protocal / Framework

&nbsp;&nbsp;&nbsp;&nbsp;It is easy to see that we need a server - client design in thie project. So, the first to consider should be **how can they communicate**, which is "what is the protocal" we can use? What framework / template to use?

&nbsp;&nbsp;&nbsp;&nbsp;For protocal, basically we have:

- Socket (TCP) Server
- HTTP Server

&nbsp;&nbsp;&nbsp;&nbsp;For frameworks, we have:

- Java.net package 
- Spring Boot (mostly for web application)

#### Server Design

&nbsp;&nbsp;&nbsp;&nbsp;To reduce requests blocking in server end, it is normal to use threads pool or create new thread for each request in the server.

&nbsp;&nbsp;&nbsp;&nbsp;According to [this tutorial](https://www.geeksforgeeks.org/runnable-interface-in-java/), there are two ways to start a new Thread – *Subclass `Thread`* and *implement `Runnable` interface*. There is no need of subclassing `Thread` when a task can be done by overriding only `run()` method of `Runnable` interface. `Thread` has a construction that accept `Runnable` as input.