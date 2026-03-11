---
title: "Streaming performances"
date: 2024-03-02T16:36:16-08:00
url: https://audiodestrukt.wordpress.com/2024/03/02/streaming-performances/
id: 1182
categories: Uncategorized
tags: 
---

# Streaming performances

I’m starting to set up a rig for doing live performance streams. In order to do this I’m feeding the output of my setup to OBS. There are a few tricks for getting this to work the way I wanted it to. The main thing is that I have a multi-channel audio interface (Focusrite Scarlett) and I want to use inputs other than the first two. For some reason OBS will only support the first two inputs of an interface out of the box. Fortunately there is an ASIO plugin available [https://github.com/Andersama/obs-asio/releases](https://github.com/Andersama/obs-asio/releases)

After installing this plugin I saw an additional audio input capture device called ASIO Input Capture which allows you to select any available input.

Capturing outputs is a little different. Apparently most ASIO devices don’t actually put data through the driver on output so even if we select an output it won’t have any audio. Newer interfaces like the 3rd generation Focusrite Scarlett seem to allow hardware loopbacks that you can set up in the driver. Otherwise there are audio loopback cables such as LoopBe and [https://vb-audio.com/Cable/](https://vb-audio.com/Cable/)

Another alternative is to use Reaper’s rearoute feature. This means you have to have Reaper running. If you want to output from the DAW this is sort of a requirement since outputs aren’t available. I’m curious if Ableton has something similar. Maybe Rewire would work for this. [https://forum.cockos.com/showthread.php?t=63358](https://forum.cockos.com/showthread.php?t=63358)

For now I have a setup with two cameras, one overhead and one facing me when I perform. So far my little SFF PC is handling things ok. I’m streaming some visuals over using NDI from another machine. I had to install the NDI plugin for OBS in order to get the visuals streaming to work. I also installed a plugin that allows me to automatically change scenes during the stream so I can move between cameras automatically. This is a key thing for doing a stream without assistance. Most DJ streams cycle between cameras and having the ability to do this on the fly is really great. The plugin is called advanced scene switcher. It takes a little configuration and is a little confusing at first. Make sure it’s actually running otherwise nothing happens!

So far OBS has been able to handle everything and now that I know about obs-asio the audio side of the equation is working out. I have the first two channels free for guitar input and I can route everything the way I need to for now.
