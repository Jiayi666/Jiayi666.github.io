---
layout:     post
title:      "Software Development LPs"
subtitle:   "Project Reflection"
date:       2022-06-09
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - Software Development
    - Reflection
---

## Software Development Leadership Principles

### It always pays off to invest time understanding the system before you start optimizing

It always pays off later to learn and understand the system before you start to design or optimizing around it. Here, "understand" means you can answer the following questions

1. The overall framework of your service, i.e. how request is received, scheduled, dispatched in the service?
2. What APIs are provided by the service? What is their contract/invariants? How is the contract preserved today?

Do not start designing or pre-mature optimizing if you don't have an answer for the 2 points above. Otherwise, even your optimization does provide some improvement,
it is very likely that you did not make the right choise between simplicity and performance or you missed some contract.

### Creating design doc over time worth it

This LP follows the idea of "understand the service before start designing/optimizing". Trying to visualize the skeleton (overall framework) of the service is a great way to
allow you to "test" if you really understand the service from a high level.

Also, it is a good way to note down the APIs and the critical resources and logic that guarantees the contracts of those APIs today. Try illustrate these critical sections
in the graph of service framework (maybe a per-API graph). It would be better to think through these things at the beginning, because you will definitely be asked about them
during the design review anyway. And understanding it early will save you a lot of time on pre-mature optimization and other mistakes.

### Favor simplicity and maintainability when it is not necessary for performance

Sacrificing the maintanability (simplicity) of the service is very very expensive. Unless you have data to support that the optimization is necessary to achieve the performance
goal and have really explored all the alternatives, we should be very careful on optimization that requires future changes to the system to take considerablly more reasoning. In
short, we always favor simplicity unless you can prove it is absolutely necessary for performance.

### Support performance optimization with data

Performance optimization that seems obvious may not give you the result you want, for example if there is another bottleneck in the system. When proposing a performance optimization,
always support it with data (eg. benchmark results). To convince others and yourself, you need to reason it in theory and support it with data.

### Try to find a governing rule, otherwise give enough detail

It would be very charming for software design if you can find a governing rule of your system, so always try to find such rule but be aware that we may very likely can't find such rule 
giving the complexity of the system.

When a governing rule can not be found, give enough details and use the "APIs of the service and their invariants" to explain how the invariants are preserved today.

### Review design early and often

Involve the main reviewer/bar-raiser of your design in the design loop as early as possible to reduce the risk of significant re-architecture in the later part of the design. This is
what we called to make the reviwer a stack holder of your design. This can be achieve by hosting "pre-review" within a small group with your key reviewers once you have a draft of
the design doc and iterate quickly on top of that.