---
title: "Using Monkey&#8217;s Audio on Linux"
date: 2011-04-17T19:41:17-08:00
url: https://audiodestrukt.wordpress.com/2011/04/17/using-monkeys-audio-on-linux/
id: 9
categories: Uncategorized
tags: 
---

# Using Monkey&#8217;s Audio on Linux

Update: I now use X Lossless Decoder for extracting .ape files on OSX. It’s nice to have the option of a native decoder.
I came across a need to extract some .ape (Moneky’s Audio) archives from Ubuntu Linux. Monkey’s Audio is a lossless .wav file compression that preserves things like Sound Forge and ACID markers. I understand now that FLAC has a mode for preserving these also, but I think that this was not the case many years ago when I first compressed the files in question for archiving.
I have performed this decompression in the past using a command called “mac” that is a native Linux version of the Monkey’s codec, but this time around I couldn’t get it installed quickly enough, so I just installed the Windows version of Monkey’s under Wine.
I didn’t know if it would work out, but it works just fine.
Install Wine:

$ sudo apt-get install Wine

Install Monkey’s under Wine by just running the installer:

$ wine MAC_410.exe

The Monkey’s Audio GUI should now be installed, and you can decompress files as you would under Windows.
Run the the GUI like this:

$ .wine/drive_c/Program Files/Monkey's Audio/Monkey's Audio.exe
