---
layout: post
title: "kill a process using port_number"
date: 2024-07-31 11:18:04
categories: ["TILs"]
---

I was working on putting together a web server then I realised I couldn't use port 8888 because of some reason. To solve this I had to find what was using the port



```
$ lsof -i:8888

COMMAND  PID USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
Python  6556 zero    7u  IPv4  0x8593e686724202a      0t0  TCP localhost:ddi-tcp-1 (LISTEN)
Python  6556 zero   10u  IPv6 0x8d6c72b61b67f0b6      0t0  TCP localhost:ddi-tcp-1 (LISTEN)
```



lsof will (list of open files) with the process that opened them with this syntax:



```
lsof -i:[port_number]
```



Now that I know the process id (PID) I can kill it using the syntax



```
kill [PID]
```



In this case its:



```
$ kill 6556
```