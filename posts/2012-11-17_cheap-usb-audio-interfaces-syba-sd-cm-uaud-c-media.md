---
title: "Cheap USB audio interfaces &#8211; SYBA SD-CM-UAUD (C-Media)"
date: 2012-11-17T17:13:20-08:00
url: https://audiodestrukt.wordpress.com/2012/11/17/cheap-usb-audio-interfaces-syba-sd-cm-uaud-c-media/
id: 438
categories: Uncategorized
tags: 
---

# Cheap USB audio interfaces &#8211; SYBA SD-CM-UAUD (C-Media)

![](images/2012-11-17_cheap-usb-audio-interfaces-syba-sd-cm-uaud-c-media_syba-usb-audio.jpg)

I’ve written a little bit about using the Raspberry PI for audio, but as you may know, the PI doesn’t support audio input. However, this is easily solved by adding a USB audio interface.

In addition to use with the Raspberry PI, I thought it would be kind of cool to have a handful of cheap audio interfaces on hand in the same way that it’s useful to have a bunch of 1/4″ adapters around.

So I started looking around at reviews for these little USB devices on Amazon. There are a ton of these around and they look to be of varying quality, so I read a lot of reviews to try to get one that wasn’t total junk. With the SYBA I almost succeeded, but not quite, as I’ll describe in a minute.

My goal was to find a USB stereo in/out audio interface that was completely inline (no cables/dongles) that was reasonably sturdy and was around 5USD.

The SYBA devices that I got mostly meet the requirements (I got mine for [6.75USD shipped from Amazon](http://www.amazon.com/gp/product/B001MSS6CS)). However, when I tried to use one with Traktor scratch I discovered that the input was only a mono input. Bummer. You can see this by looking in ASIO4all or by looking at the driver in Windows. Many times I’ll see an onboard audio input configured as a mono input where it actually supports stereo. I thought that this might be one of those cases where all I needed to do was enable the stereo profile in the WDM driver, but alas, this was not the case.

On the plus side, these are surprisingly well made and otherwise work very well. The headphone output is very loud though and I’m worried that it might be somewhat distorted. I didn’t notice any problem when I connected my studio monitors though. I’m getting a small amount of digital noise at the output, but my current audio laptop is a little bit noisy in general so it might be better with another machine.
