---
layout: post
title: "EXIF Remover Desktop App"
date: 2025-11-25 00:04:04
categories: ["photography", "privacy", "tools"]
---

**UPDATE**: This was replaced with a progressive web app (PWA) because that's easier to use and main cross platforms. Source here <https://github.com/bmwasaru/Scrub-Metadata>



Spent some time building a desktop app to help me remove EXIF data from my photographs before posting them online. This matters to me because I don't want to be profiled based on the location, time and even the device I use to take the photos on. Also the other thing that matters is I wouldn't want to expose others through the location data that may be included in the photographs.



If you look at the info section of the photos on my previous post here <https://britone.xyz/2025/10/06/at-the-workshop/> you might catch the data that was uploaded with the photos. Data such as the phone type and the app that I used to take the photo. Previously, I had worked on an AppleScript (<https://britone.xyz/2024/11/11/remove-exif-data-on-macos/>) to help with cleaning of data but that was not very intuitive.



For the technicalities about the development; its build using electronjs meaning its cross platform out of the box. All you need is to run the build.sh command to generate the assets (apps) for MacOS, Windows and Linux platforms. The code is open sourced on my GitHub account here <https://github.com/bmwasaru/exif-scrubber>



Here is how it looks on the desktop:


[![](/assets/images/screenshot-2025-11-24-at-23.58.37.png)](https://bmwasaru.wordpress.com/wp-content/uploads/2025/11/screenshot-2025-11-24-at-23.58.37.png)