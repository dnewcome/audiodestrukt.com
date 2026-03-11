---
title: "Overview of free MIDI editors"
date: 2024-01-26T13:58:43-08:00
url: https://audiodestrukt.wordpress.com/2024/01/26/overview-of-free-midi-editors/
id: 1009
categories: Uncategorized
tags: 
---

# Overview of free MIDI editors

I’m doing research for a MIDI sequencer project now that I’ve had on the back burner for ages. Over the years I’ve dug around the internet to find examples of small MIDI apps sort of like Seq24. I’m going to post a few things here that I’ve found mostly because I forget that I even looked at them much less what I thought of it or even if I got it to build and run.

Some projects have painfully generic names, and [https://midieditor.org/](https://midieditor.org/) is one of them. I did get this to build from source. It is built on QT5 and uses qmake for building. I got some warnings and the build script didn’t work as-is on my linux box but I got it to work by running qmake by hand and building with make.

I grabbed the source code from here [https://github.com/markusschwenk/midieditor](https://github.com/markusschwenk/midieditor)

![](images/2024-01-26_overview-of-free-midi-editors_image.png)

This is a really basic sequencer. I’m not sure why I like messing with these little things so much. Maybe it’s to figure out what really is essential when building something like this.

There are some commandline tools I’ve been looking at as well like midish [https://midish.org/](https://midish.org/)
