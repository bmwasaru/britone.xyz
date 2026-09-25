---
layout: post
title: "Fix: ValueError: unknown locale: UTF-8"
date: 2020-05-06 01:30:07
categories: ["Django"]
tags: ["bash", "python"]
---

I was setting up the [python.org](http://python.org) website code, built on Django, on my local machine I encountered the error `ValueError: unknown locale: UTF-8` while running the `./manage.py migrate` command. See screenshot below:
![Screenshot 2020-05-06 at 01.06.57](/assets/images/screenshot-2020-05-06-at-01.06.57.png)
To fix this, I had to set the following environment variables:
`export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8`
There, back to code.