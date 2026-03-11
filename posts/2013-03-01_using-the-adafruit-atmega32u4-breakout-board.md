---
title: "Using the Adafruit Atmega32u4 breakout board"
date: 2013-03-01T19:10:31-08:00
url: https://audiodestrukt.wordpress.com/2013/03/01/using-the-adafruit-atmega32u4-breakout-board/
id: 585
categories: Uncategorized
tags: 
---

# Using the Adafruit Atmega32u4 breakout board

I picked up an Atmega breakout board from Adafruit the last time I ordered from them. I haven’t had much of a chance to use it yet other than to blink a “hello world” LED, but I wanted to make a few notes here about it to keep my memory fresh. Hopefully it helps you guys out too.
One of the reasons that I was interested in this board is that it uses one of Atmel’s USB-equipped chips, the 32u4. If I remember correctly this chip is not available in a DIP package, only SMT, so you can’t just swap it into an Arduino board. I’m interested in using these chips in my audio designs since you get USB for free. There are some USB class-compliant MIDI firmwares for this family of devices so I think it’s ideal for audio hacks.
The newer Arduino boards actually use this chip family (8u2) in place of the old FTDI USB controller chip. With some creative firmware flashing it’s possible to make the Arduino look like a class compliant  MIDI device. I used this LUFA-based Uno firmware with some success in the past. Unfortunately it can be hard to get the Arduino back to factory settings if you do this and you don’t have a real device programmer. I had to resurrect my Arduino using a Bus Pirate as an Arduino programmer. Which, by the way was pretty slow. There are some speed patches available, but it has been a while since I looked at this stuff so I don’t know the state of this situation. With the breakout board I think we have to use LUFA MIDI capabilities directly.
So back to the board. There are some other advantages to this breakout over the Arduino. It’s smaller, it plugs directly into a breadboard, and it is cheaper. I think if you really wanted to you could just design your final board layout to have this thing just soldered right on. For low-volume prototypes this might make a lot of sense if you want to avoid SMT work.
The downside is that this isn’t an Arduino. You don’t get the Arduino software stack. Although there is Teensyduino if you really want to run Arduino on the Teensy-compatible boards. Adafruit doesn’t recommend this for some reason though, and I have never tried it.
I think between the nice avrdude-compatible boot loader and the USB class-compliant software libraries available though, this should make doing custom MIDI devices pretty straightforward still.
