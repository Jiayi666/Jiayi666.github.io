---
layout:     post
title:      "Scale From Zero To Millions Of Users"
subtitle:   "System Design - An Insiders's Guide - Chapter One Notes"
date:       2023-09-17
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - System Design
---

## Software Scaling Principles

### Scale The Service

* Breakdown functionalities so different components can be scaled independently
* Load balancing smartly to allow request from a single customer can be processed by multiple servers
* Use multiple caching layer to serve customer requests in early layers to avoid traffic in backend components
* Introduce data/server replication to avoid SPF (single point of failure)
* Respect geographical distribution of customers and use CDN (also a type of caching) or even serve customer from multiple data centers from different geometrical regions

### Scale The Operation

* Automate the operation when system gets bigger
* Develop tools for monitoring and logging
* CI/CD development process
* Develop tools for testing

## Frequently Used Abstractions For Scaling

### Load Balancer

* Geometrical distance based LB (CDN is one of them)
* Message queue
* Sharding
* Stateless LB -- this worth a few more words. It is important to make each component itself stateless in terms of "customer info (eg. web browser cookie)" so any server can process request from any customer. This can be achieve by storing customer info in a side data base (probably Non-SQL) and make the server read from there.

### Caching

* CDN (content delivery network)
* Write through caching
* Read through caching

### Database

* SQL (relational)
* Non-SQL (unrelational)

## Interesting Scenarios To Think About Scaling

* One dominant customer drives most of the traffic for the system
* Maintain availability and durability is also something to consider when scaling a service
