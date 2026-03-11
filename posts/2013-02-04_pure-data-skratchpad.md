---
title: "Pure Data Skratchpad"
date: 2013-02-04T20:48:14-08:00
url: https://audiodestrukt.wordpress.com/2013/02/04/pure-data-skratchpad/
id: 571
categories: Uncategorized
tags: 
---

# Pure Data Skratchpad

I just released a first version of a Pure Data patch that I’ve been playing with called Skratchpad. The basic purpose of this patch is to enable manipulation of an audio loop using a turntable and a trigger pad.
Lots of DJs are using things like the Novation Dicer to manipulate cue points and trigger samples. I don’t have a Dicer but I have my NanoPad, which I use to trigger things in a similar way.
I demo the patch in this video:

The functionality is pretty basic right now, but I’m planning on adding live resampling features to it soon, since one of the things missing from most looper/chopper applications is the use of live audio or reslicing the current output of the app.
If I can get my hands on a USB DJ interface I might try adding support for jog wheels instead of timecode vinyls. Some other features that would be nice is the ability to set/remove cue points instead of having a few presets. Right now the loaded loop gets divided up into 4 equal sections. This works for a lot of drum breaks, but there can be issues with timing and clicks/pops in the audio if the cue point happens in the wrong spot.
This is a really basic start that should be easy to build on in the future.
