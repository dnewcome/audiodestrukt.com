---
title: "Running Reaper in Headless Mode"
date: 2024-02-01T12:27:46-08:00
url: https://audiodestrukt.wordpress.com/2024/02/01/running-reaper-in-headless-mode/
id: 1080
categories: Uncategorized
tags: 
---

# Running Reaper in Headless Mode

I’ve recently needed to run a headless mixer on my machine. I spent a lot of time looking into various things like trying to use Non mixer and a few other things like python libraries to build a virtual mixing console in code. This stuff all kind of either got too involved and complex or just didn’t work. Ideally I would have a fancy audio interface with more advanced mixer capabilities that can be configured with software and then run standalone, but I don’t have anything like this at the moment that meets my needs although the M-Audio 2626 has some of this functionality as does the MOTU 828MKII. It’s just a little fiddly for me right now.

I thought it would be cool to just use a DAW and currently I’m using Reaper set up with my desired routing. I’d like to not even have the GUI distracting me though and I looked into running it headless. Turns out that it’s possible on Linux only by recompiling libswell.so with some flags.

The trick is outlined here https://forums.cockos.com/showthread.php?p=2529113

Passing NOGDK=1 into the build of libswell does the trick. There are some warnings generated and by default GCC treats these as errors. So it’s essential to also set -Wno-error. I did this by modifying the makefile but it’s just as easy to pass in the environment.

It’s worth noting that libswell is part of the WDL library from Cockos. After building I just copied libswell.so over into my downloaded Linux install of Reaper.

Audio settings are saved in reaper.ini according to this https://forum.cockos.com/showthread.php?t=254769

So far so good. I haven’t used it yet but at least it appears to be working as expected.
