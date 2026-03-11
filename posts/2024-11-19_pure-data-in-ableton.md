---
title: "Pure data in Ableton"
date: 2024-11-19T15:51:13-08:00
url: https://audiodestrukt.wordpress.com/2024/11/19/pure-data-in-ableton/
id: 1332
categories: Uncategorized
tags: 
---

# Pure data in Ableton

I’m messing around with PD again after what feels like years. I have PlugData installed and I’m messing around with it.

I tried adding a noise generator like this:

![](images/2024-11-19_pure-data-in-ableton_image_2024-11-19_153656082.png)

Note that the volume is turned down by default. In order to hear anything I had to turn up the volume slider. DSP was turn on when I added the out~ module though.

Adding a lowpass filter to the noise is no problem.

![](images/2024-11-19_pure-data-in-ableton_image_2024-11-19_153920494.png)

I wonder if we can do midi learn on the knob? Doesn’t seem like it.

Automation params can be mapped by receive symbol. Adding a new float object and a new parameter. We can link them using this symbol

There is a compiled mode using the HVCC compiler [https://wasted-audio.github.io/hvcc/docs/01.introduction.html](https://wasted-audio.github.io/hvcc/docs/01.introduction.html)
