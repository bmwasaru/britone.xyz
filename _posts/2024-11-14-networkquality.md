---
layout: post
title: "networkquality"
date: 2024-11-14 19:46:39
categories: ["macOS", "TILs"]
---

Today I learned that MacOS has an inbuilt command `networkquality` that can use can you to test your internet speeds without using speedtest.net or fast.com. You type it in the command line and while running it will display the Downlink, Uplink speeds:



```
$ networkquality
Downlink: 3.958 Mbps, 37 RPM - Uplink: 8.765 Mbps, 37 RPM
```



You can stop it using Ctrl+C but if you let it run for a few seconds it will end with a summary as shown below



```
==== SUMMARY ====
Uplink capacity: 7.997 Mbps
Downlink capacity: 5.332 Mbps
Responsiveness: Low (1.071 seconds | 56 RPM)
Idle Latency: 104.417 milliseconds | 576 RPM
```



I'm thinking this might be a way that maintains privacy without having to visit some ads serving speed testing website.