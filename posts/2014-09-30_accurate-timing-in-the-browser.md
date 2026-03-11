---
title: "Accurate timing in the browser"
date: 2014-09-30T10:56:00-08:00
url: https://audiodestrukt.wordpress.com/2014/09/30/accurate-timing-in-the-browser/
id: 829
categories: Uncategorized
tags: 
---

# Accurate timing in the browser

I have been playing around with some simple audio stuff in the browser and Nodejs again lately. In the past I’ve done some experiments with generating audio and doing simple sequencer UIs, but I never tried to get something really useful happening.
One thing that’s crucial for playing audio events is timing. When generating actual audio  waveforms, this was easy since everything was sample accurate, but when playing back audio samples according to a sequence, timing is very  critical and as it turns out, tough to get right in the browser. The reason for this is that the default timing go-to is setTimeout/setInterval, which is very inaccurate.
In my searches, some people are trying to create high resolution timers using window.performance APIs. Others are doing some interesting tricks to smooth things out either by diffing the time since the last event or doing a low-resolution setTimeout and then polling.
The best solution I’ve seen uses the Web audio APIs createBuffer() to create sample-accurate callbacks. I encourage you to check out the source, but the crux of the timing technique is to create a buffer of the exact length and rate, start it and register a callback when it ends.

source.buffer = context.createBuffer(1, 32000 * (length / 1000), 32000);
source.onended = callback;
source.start(0);

The sample rate here is 32000 samples/second. The first argument to createBuffer is the number of channels. We calculate the tick length in samples and register a callback.
I’m going to be reading through more of this code and using some of these timing techniques.
