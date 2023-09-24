---
layout:     post
title:      "Design A Rate Limiter"
subtitle:   "System Design - An Insiders's Guide - Chapter Four Notes"
date:       2023-09-24
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - System Design
---

## Where To Put A Rate Limiter

It seems like a good idea to always start with the simplist "client <--> server" model (only 2 component, a client and a server). So a rate limiter can be implemented in

1. The client side
2. The server side
3. In between of client <--> server

Today in many cloud based design (microservices) the rate limiter is implemented in the "API GateWay" layer, which is a layer between client and server for security and authentication. The API gateway may sounds similar as a load balancer but they are different

* API Gateway - focus on authentication and security, most cloud provider allows setting rate limitting rules as well
* Load Balancer - focus on distributing client requests to servers

## Algorithms

* **Token Bucket** : every request cost a token, tokens are filled with constant rate, tokens can be accumulated up to the bucket size to allow bursting traffic
    * Pros -
        * allows bursting traffic
        * memory effcient -- only need to store the current token count
    * Cons -
        * two parameters (bucket size + refill rate) making it harder to tune
* **Leaking Bucket** : a new request is added to a FIFO queue (the "bucket") and rejected if bucket is full, requests in the buckets are processed at **a constant pace**
    * Pros -
        * allows bursting traffic tho they may not get processed immediately
        * memory efficient given a limitted queue size and in many case the queue is the same one for multi-threading
        * delivers **const request processing rate** so suitable for service requires that
    * Cons -
        * two parameters (bucket size + processing rate) making it harder to tune
* **Fixed Window Counter** : count requests processed during a "time window" and reject request if the requests processed during the window reached max
    * Pros -
        * memory efficient -- only need to store the count for current window
        * easy to implement
        * only one parameter
    * Cons -
        * does not support bursting requests
        * if 2 burst happened just between the edge of the window, the actual rate around the "window change" time can be higher than allowed
* **Sliding Window Counter** : keep the number of requests processed in past minute and the requests processed so far in current minute, then calculate current count as a weighted average between request from past min and this min with the weight as **"how long we have spent on this min"**. For example if it has been 20s in the current minute then `current_count = (20s/60s) * this_min_count + (40s/60s) * past_min_count`
    * Pros -
        * support bursting request -- the bursting requests are **"smoothen"** in this algorithm
        * memory efficient -- only need to store the count for past and current time slot
        * easy to implement
        * only one parameter
    * Cons -
        * the current counter is a weighted average and is not super precise. Based on some use case it is reported that the error case of a sliding window counter throttling is less than 1% among 400 million request

## Make The Solution Scalable

Making the rate limiter to be able to control a distributed system is significantly harder. But the following mental process may still be useful

1. The first step is always to find an idea (or some ideas) to **"make it work"**
2. Then we can start thinking of ways to **optimize it** either in terms of performance or cost

### Make It Work

The most obvious challenge for a distributed rate limiter is that no matter what algorithm you use, you will need a **centralized place to store the counter**. If you can find such place, and **make the counter support atomic operations** then the above algorithm will still work with almost no adjustion.

### Opotimize It

To optimize a problem, the most important thing is to understand **WHAT YOU CAN COMPROMISE and WHAT YOU CAN NOT** in this design. Here for the rate limiter

* **CAN** compromise
    1. If count value is dropped (for example the value is not duplicated) we can easily start from 0 again which is not a big deal if we let by a bit more traffic for a few seconds
    2. If the check and edit of the count value is not strictly CAS which risk as let a few requests pass through the limiter which is also not a big problem
* **CAN NOT** compromise
    1. The rate limiter must be fast enough

As a result, we do not require strong durability or consistency for the counter so the following optimizations can be considered

1. Use memory-cached centralized storage such as [Redis](https://redis.io/) which flush in-memory data to disk periodically but for all customer I/O it serve directly from memory
2. Allow rate limiter to do "read + atomic increase" instead of a CAS because a CAS is very likely to fail under high IOPS scenario
3. Leverage geometric distribution of Redis servers to minimize network cost for rate limiter

## Close The Loop

After designing the rate limiter, make sure to remember to **HANDLE THE ERROR PROPERLY** at the client side.


