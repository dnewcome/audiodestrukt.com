---
title: "Network audio with NetJack part II"
date: 2013-02-06T02:08:08-08:00
url: https://audiodestrukt.wordpress.com/2013/02/06/network-audio-with-netjack-part-ii/
id: 576
categories: Uncategorized
tags: 
---

# Network audio with NetJack part II

In the last installment I was setting up Jack on different platforms, namely Mac and Windows in preparation for doing some network streaming. Jack was kicking butt locally on both platforms using ASIO and CoreAudio as the case may be.

However I hate to be the bearer of bad news – when I went to stream the audio over the network, the fairy tale came to an end.

As a little background, I’m trying to get some sort of low-latency audio stream happening on a local network having relatively high bandwidth. My thoughts were that Jack had the most promise and flexibility. I was right about the flexibility part, but wrong about the promise. 

The way that the Jack architecture works is that any networked audio done using Jack is actually handled by a Jack client. Lots of different programs can be clients, and they show up and register themselves with the Jack daemon when they are run. The streaming source runs a Jack client called jack_netsource and the listener runs Jackd with the netone audio backend enabled.

When netone is used, Jackd listens on UDP port 3000

```

retnex:single-step dan$ lsof -P -iUDP | grep jack
jackdmp 22690 dan 0u IPv4 0x3e86a3266c10ae7 0t0 UDP *:3000
jackdmp 22690 dan 5u IPv4 0x3e86a3266c12b0f 0t0 UDP *:*

```
Connecting from Windows to Mac worked somewhat, but connecting the other way did not work at all. I can’t find my notes from this experiment so I’m not sure exactly what the errors I was getting were.

So netjack is a bust, what about other Jack clients? 

Well I tried to build VLC with Jack enabled for Windows. This doesn’t seem to be supported at all. It should work in theory, but the build system doesn’t include libjack and I didn’t feel like trying to build VLC this way.

I tried a few other things like Gstreamer and ffmpeg Jack clients, but I just wasn’t able to get any of these things working.

GStreamer and ffmpeg on their own seem promising though, just not as Jack clients.

In a future post I’ll talk a little bit about GStreamer et. al. and how I finally got something working over the network.
