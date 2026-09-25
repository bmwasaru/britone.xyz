---
layout: post
title: "mkdir and cd"
date: 2025-11-26 16:19:00
categories: ["bash", "scripting"]
---

Here is a bash function I recently added to my dotfiles specifically .bashrc



```
function mcd() {
    mkdir -vp "$1"
    cd "$1"
}
```



To use this on my terminal, I need to export this in the same .bashrc file



```
export -f mcd
```



So from the command line, I can create and immediately change to the created directory.



```
mcd name_of_new_folder
```