---
title: "Hacking on the APC 20"
date: 2012-11-26T00:45:45-08:00
url: https://audiodestrukt.wordpress.com/2012/11/26/hacking-on-the-apc-20/
id: 466
categories: Uncategorized
tags: 
---

# Hacking on the APC 20

I recently got an AKAI APC 20 Ableton control interface at a local used music store. I have been hunting around for one of these pad-style controllers for a while, and this one was priced right.

I don’t think I’d ever buy a Monome, mostly due to the price, but the controller market seems to be heating up and there is a new one on the market every few months it seems.

Something to note about the APC is that while it is fully MIDI-compliant, it has a few operating modes that are set via SYSEX commands.

When the controller is connected to Ableton, it goes into an Ableton Live mode where all of the lights are controlled by software. When the device is first powered up and not conneted to any software it goes into a default mode where the clip launch pads trigger a green light when pressed and the small channel buttons at the bottom are latched buttons that turn on and off when pushed.

I first used this with FL Studio, which apparently supports the device so well that it has its own set of note pages that give you some different interesting mappings. At first I thought that these modes were baked into the device, but they are obviously not, as the modes are only available when paired with FL Studio.

If the APC just sits there without a USB connection it will start to display a sort of screensaver pattern with chasing lights.

Here are the SYSEX commands that can be sent with a tool like MIDI OX.

The handshake query identifies the device and polls things like the firmware revision:

```

0xF0, 0x7E, 0x00, 0x06, 0x01, 0xF7

```
The device mode set sysex can put the device into one of four modes based on the value of the 7th byte in the following message:

```

0xF0, 0x47, 0x7F, 0x7B, 0x60, 0x00, 0x04, 0x41, 0x08, 0x02, 0x01, 0xF7

```
0x40 is the default startup mode, 0x41 is Ableton mode. The APC20 has a fourth mode called note mode corresponding to 0x43. I’m not sure what this mode is useful for yet, as mode 0x41 seems to be the most useful for programming since it relinquishes full control over the device.

I’ll be posting more about this as I find out more.
