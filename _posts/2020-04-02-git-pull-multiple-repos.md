---
layout: post
title: "Git pull multiple repos"
date: 2020-04-02 11:02:34
categories: ["git"]
tags: ["bash", "scripting"]
---

I read a lot of open source projects, this has helped learn how to write code better. One of the interesting projects I follow is sentry (https://github.com/getsentry/sentry), sentry is cross-platform application monitoring, with a focus on error reporting.
The one challenge I have had is keeping up with the repositories, I needed a way to keep the repositories on my laptop up-to-date. Here is a one liner bash script I use to git pull the multiple repositories.
`for i in */.git; do ( echo $i; cd $i/..; git pull; ); done`