---
layout:     post
title:      "Back-Of-The-Envelope Estimation (aka Napkin Math)"
subtitle:   "System Design - An Insiders's Guide - Chapter Two Notes"
date:       2023-09-23
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - System Design
---

## Some latencies programmers should know

```
Latency Comparison Numbers (~2012)
----------------------------------
L1 cache reference                           0.5 ns
Branch mispredict                            5   ns
L2 cache reference                           7   ns                      14x L1 cache
Mutex lock/unlock                           25   ns
Main memory reference                      100   ns                      20x L2 cache, 200x L1 cache
Compress 1K bytes with Zippy             3,000   ns        3 us
Send 1K bytes over 1 Gbps network       10,000   ns       10 us
Read 4K randomly from SSD*             150,000   ns      150 us          ~1GB/sec SSD
Read 1 MB sequentially from memory     250,000   ns      250 us
Round trip within same datacenter      500,000   ns      500 us
Read 1 MB sequentially from SSD*     1,000,000   ns    1,000 us    1 ms  ~1GB/sec SSD, 4X memory
Disk seek                           10,000,000   ns   10,000 us   10 ms  20x datacenter roundtrip
Read 1 MB sequentially from disk    20,000,000   ns   20,000 us   20 ms  80x memory, 20X SSD
Send packet CA->Netherlands->CA    150,000,000   ns  150,000 us  150 ms

Notes
-----
1 ns = 10^-9 seconds
1 us = 10^-6 seconds = 1,000 ns
1 ms = 10^-3 seconds = 1,000 us = 1,000,000 ns

Credit
------
By Jeff Dean:               http://research.google.com/people/jeff/
Originally by Peter Norvig: http://norvig.com/21-days.html#answers

Contributions
-------------
'Humanized' comparison:  https://gist.github.com/hellerbarde/2843375
Visual comparison chart: http://i.imgur.com/k0t1e.png
```

### What we know from the above data

1. Memory >>> SSD >> Disk
2. A simple compression is fast, compress data before send over the wire may be beneficial
3. Cross region network is very slow

## About "peek average"

One often asked question during interview is "peek QPS (Qerry Per Second)" or "peek IOPS" given the information like 

1. Total active users, say 300 million
2. Average daily active users, say 50% of total active user
3. Average post per day (assume one post result in one querry), say 2 posts per day

Then the `QPS = 300M * 50% * 2 / (24 * 3600s) = 3500 / s`. Then what is the "peek QPS"? This is a concept I have not really understand.

* If we want to know the actual max then you either need to look at the throttling in your system or really calculate with "max (both active + inactive) user" and "max post a use can possibly send in a second"
* But most of the case, if you are just look for a rough idea of **"what is the QPS that the system must can handle as a system design lower bound"** then you can just look at the factor that is **most likely to change**. And in our example, that factor is "daily active user" because 
    1. That is the only data we have in this question :)
    2. It seems to be easier that more user come online one day for some event than all user starts to post more frequently 

So for estimating a "lower bound" for how many requests the system at least need to be able to handle, it can just be `peek_QPS = QPS / (50%) = 7000 / s`.