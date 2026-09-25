---
layout: post
title: "remove exif data on MacOS"
date: 2024-11-11 14:06:32
categories: ["macOS", "TILs"]
---

I was look at how to remove [exif](https://en.wikipedia.org/wiki/Exif) data from photos I had copied to my Mac. I used [AppleScript](https://en.wikipedia.org/wiki/AppleScript#:~:text=AppleScript%20is%20a%20scripting%20language,package%20of%20system%20automation%20tools.) to achieve this:




https://gist.github.com/bmwasaru/f4f4242bfe29418a77fc2e0b5e74f59c




To use this:



1. Open **Script Editor** on your Mac (found in Applications > Utilities).
2. Paste the script
3. Hit the run button



This script lets you select one or more images, uses the `sips` command with the `-s formatOptions none` option to remove the metadata. It makes a backup copy of the image with `.backup` extension.