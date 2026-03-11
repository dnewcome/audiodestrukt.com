---
title: "MIDI software roundup"
date: 2012-11-26T20:57:51-08:00
url: https://audiodestrukt.wordpress.com/2012/11/26/midi-software-roundup/
id: 468
categories: Uncategorized
tags: 
---

# MIDI software roundup

I’m doing a quick post on my current MIDI software setup on my audio laptop currently – partly for me and partly for you. I seem to forget which bits of software I’m using during a particular period of time, DAW-epoch if you will.

In the dark ages I used to use Hubi’s MIDI loopback driver, but that’s pretty much ancient history now. Somehow I keep thinking that’s what I’m looking for, when in reality I want [MIDI Yoke](http://www.midiox.com/).

So, for MIDI general transformation/mapping duties, managing sysex dumps and all-around MIDI debugging, nothing beats MIDI-OX, from the same author as MIDI Yoke. There is a purportedly more powerful MIDI translation program called [Bome’s MIDI Translator](http://www.bome.com/products/miditranslator) as well, but I have not actually needed it yet. If you are on Mac Bome’s is pretty much the only game in town.

For crazier MIDI mappings, and/or anything that needs to interface with HID devices (joysticks, etc.) [Pure Data](http://puredata.info/) is my go-to tool. The learning curve is pretty huge compared to doing simple mappings in MIDI-OX, but once you get to a certain level of complexity in your mappings MIDI-OX starts to get really tedious, and IMO, it’s time for PD.

Recently I’ve become aware of some other MIDI loopback software, such as Tobias Erichsen’s [loopMIDI](http://www.tobias-erichsen.de/software/loopmidi.html). I have not tried this out, but Tobias is also the author of a really interesting bit of software that provides a Windows rtpMIDI driver that is supposedly compatible with iOS/Mac OS network MIDI. This could mean that iPad apps can do network MIDI with a PC.

NTONYX, of Virtual Audio Cable fame, has the [MIDI Matrix](http://www.ntonyx.com/mm10.htm) app, which is able to virtually connect port together, something that MIDI Yoke cannot do on its own.

I’ve started doing some MIDI programming in Ruby also, using the fantastic [unimidi](http://rubygems.org/gems/unimidi) library, which appears to work well in Windows. I have de-facto decided to avoid special-purpose programming languages like [KeyKit](http://nosuch.com/keykit/) for now although if there is anything I can’t manage in Ruby I may branch out a bit.
