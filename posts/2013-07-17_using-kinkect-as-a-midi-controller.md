---
title: "Using the Kinect as a MIDI controller"
date: 2013-07-17T22:40:02-08:00
url: https://audiodestrukt.wordpress.com/2013/07/17/using-kinkect-as-a-midi-controller/
id: 776
categories: Uncategorized
tags: 
---

# Using the Kinect as a MIDI controller

I just grabbed a Microsoft Kinect camera from eBay. I’m new to the 3d camera thing so I wanted to get something cheap and simple to start out with.
There are some things to keep in mind when getting a Kinect to work with a PC or Mac. The particular version of Kinect is important as it will dictate what kind of power adapter you need. Although the Kinect is a USB device, it requires extra power. The older Kinects had a separate power supply, but the newer “slim” devices use a single cable that looks a bit like USB but isn’t. Lots of third parties sell a little power adapter that will power the device and split the USB connector out.
I wanted to do a quick test to make sure everything was working so I grabbed Gesturement and installed it on my Mac.
I had to play around with the depth control a lot to get it working but once I had things set up I could generate MIDI CC messages by moving my hands around.
It seems like this should all be possible with a normal camera and OpenCV as well, but at least I know my used Kinect is working ok.
