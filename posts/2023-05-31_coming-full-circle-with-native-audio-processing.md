---
title: "Coming full-circle with native audio processing"
date: 2023-05-31T08:59:28-08:00
url: https://audiodestrukt.wordpress.com/2023/05/31/coming-full-circle-with-native-audio-processing/
id: 522
categories: Uncategorized
tags: 
---

# Coming full-circle with native audio processing

I wrote the following in 2012 and just found the draft. Did this come to pass? I think some hardware we are seeing now could be seen as general purpose computers repackaged as single-purpose audio devices.
===
I’ve been thinking about the divide between using general purpose computing platforms vs using dedicated hardware for a long time now. As long as I’ve been using software for making music. There have always been arguments for and against doing things like synthesis in hardware vs using software plugins.
However, as time goes on more and more hardware devices are just specialized computing platforms designed to run certain software. Even devices that use dedicated DSPs are relatively general purpose, as the software is usually loaded into the RAM of one of a few limited DSP architectures available.
Once general purpose computing platforms became capable enough to run algorithms that would have required specialized DSP hardware the question became one of stability and convenience rather than sound quality.
The biggest thing that dedicated hardware has going for it is that since it is purpose-built for one thing, it is more stable and usually has better latency characteristics. Setting up audio processing on general purpose operating systems often requires tradeoffs and tweaks to improve performance, and you can only go so far in some cases, as general purpose OSs are not designed to be realtime systems.
The relatively high cost of general purpose platforms (e.g., high-end laptops) encourages multi-purposing the hardware. That is, trying to run many things on the same hardware at the same time. With dedicated hardware this is not an issue, since it generally is not reconfigurable to run things in parallel on the same hardware. For example, you won’t be able to load a Nord Lead into a Virus synth and play them at the same time.
So, here is my theory regarding native processing. I think that the price of general purpose platforms is going to make this argument mostly all in favor of native processing. Laptops are already cheap enough that one might purchase one just to run some software such as NI Reaktor. Once the system is set up and optimized it won’t be used for anything else. This option is only attractive as long as the hardware is cheap enough.
However, what if we take an extreme case, such as the Raspberry PI? Supposing that the PI could run something like Reaktor (it can’t currently, but let’s assume that at some point in the future, some general purpose device like the PI, costing under 50USD is capable of running Reaktor) why not optimize a device that runs Reaktor and sell it pre-configured, or offer some configuration recipe for the device?
I think you can see where I’m going here. As platforms become cheaper we can treat them as a commodity. One of the things preventing us from doing so currently is custom configuration. It is hard to get audio working well on general purpose devices, but it is possible and people do get it to work well. Possibly the solution is to treat these configurations as containers that can run on general purpose devices.
Would you buy a Reaktor container for a 50USD hardware device if you knew you’d get perfect performance out of it? People certainly bought the Nord Modular system and paid many thousands of dollars for it in many cases.
