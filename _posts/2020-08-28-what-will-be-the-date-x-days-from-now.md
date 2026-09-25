---
layout: post
title: "What will be the date x days from now?"
date: 2020-08-28 05:58:48
categories: ["scripting", "sql"]
---

Today I learn some nifty shell command. The command simply answers the question, what will be date x days from now. So lets says I wanted to know what will be date and time 13 days from now
`echo "select now() + '30 days'::interval" | psql`
As you can see from this I am piping into psql (postgresql terminal frontend) so this is simply a SQL statement run from the shell.