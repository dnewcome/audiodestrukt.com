---
title: "Behringer FCB1010 configuration notes"
date: 2012-04-28T18:44:24-08:00
url: https://audiodestrukt.wordpress.com/2012/04/28/behringer-fcb1010-configuration-notes/
id: 241
categories: Uncategorized
tags: Live PA
---

# Behringer FCB1010 configuration notes

I just got an FCB1010 to add to my live rig and I figured I’d be stomping away by now, but apparently I didn’t look into exactly how this pedal was designed before I got it. It turns out that it works entirely differently than I was expecting. At first I was really upset and I was going to send it back, but after reading around on the net I’m thinking that I’ll try to get it working in my rig.

For those of you following along at home, I thought that I’d be able to have 100 sets of configurable Midi switches to play with. That is, I want to have one set that sends note events like a keyboard, and maybe a bank to control my sequencer transport, that kind of thing. However, this is not how the pedal was designed. This thing is designed to switch settings on a complex guitar rig. Each one of the foot switches is really just designed to select a specific setting on a guitar amp.

My first indication that things were completely different than my expectation was that I couldn’t figure out how to get the pedal out of “preset select” mode. That is, no matter what I did, the thing was always switching to a different preset when I hit a foot switch. There didn’t seem to be any way to just get the foot switches to do what they were programmed to do (send a Midi note, CC, etc). This was fundamentally incorrect assumption number one. In fact there is only one mode, and that was it. You are always just selecting some preset with the pedal.

The upshot is that these presets can be very sophisticated, sending multiple messages at once when selected. However the second thing I ran into initially was that the expression pedals weren’t sending any data when I moved them. I’m using Midi-OX to monitor the data so presumably even if the pedals were sending some kind of bizarre Behringer-specific sysex stuff I should see it there. But — nothing. Just nothing was getting sent. I went through the programming steps to make sure that some control message was actually assigned to the pedal and still nothing.

It wasn’t until I read some of the reviews that I realized that many people had to run the calibration/self-test routine in order to get the CC pedals working. [So I did that](http://host.mtnsys.com:81/faq-fcb/PedalCalibration.htm) and thankfully the expression pedals started working. Somehow it just doesn’t seem right that I didn’t get anything at all until I did the calibration. That just sucks. I’d have preferred getting kind of out-of-range data at first and then I’d realize that I needed to calibrate it. I almost sent this thing back because I couldn’t get the pedals working. I wonder how many returns that have because people don’t figure this out.

There is an [aftermarket firmware](http://www.ossandust.be/faq.php) that allows something called stompbox mode that lets you use the pedals as individual switches (almost) like I wanted to, but I don’t really want to have to do a firmware swap just to get this working how I want it. Anyway, after reading some forum posts about how people have their foot pedals set up I realized that I can probably get the FCB working with my rig. The difference between what I was thinking and the way that I’m probably going to have to do this is that I’m going to have to set up a preset for each single action that I want. This means that I’m going to have 10 presets for a Midi keyboard that sends note events. There will be one preset for each single note, or an entire bank devoted to just providing Midi keyboard functionality. Fortunately there is a “tap-tempo” feature that allows you to send note-on and note-off events with a key. If it weren’t for this feature I’d be doing a lot of hacking around with filtering rules in Midi-OX.

Hopefully this helps any would-be FCB1010 owners. This [forum post](http://forum.cockos.com/showpost.php?p=368549&postcount=2) helped me figure out that I was thinking about this all wrong, and [this thread](http://www.circularlabs.com/forums/showthread.php?t=326) helped me figure out how I was going to approach my configuration now that I realized I had it all wrong.
