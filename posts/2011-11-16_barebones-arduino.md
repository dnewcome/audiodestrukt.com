---
title: "Barebones Arduino"
date: 2011-11-16T13:21:49-08:00
url: https://audiodestrukt.wordpress.com/2011/11/16/barebones-arduino/
id: 91
categories: Uncategorized
tags: 
---

# Barebones Arduino

While waiting for my Arduino Uno to show up, I thought I’d explore the Arduino ecosystem a little bit. I had an Atmega48 chip lying around and I wondered if I could get it working to play around with AVR development in the meantime to familiarize myself with things a bit.
After some research, I found that I should be able to get some Arduino stuff working on it without a full Arduino board. It is helpful to know what Arduino actually is. Roughly, it is a C API that is modeled after Processing. The toolchain uses gcc-avr and links to a small libc for AVR microcontrollers. The IDE is set up to make this toolchain integrated and easy to use. The Arduino stack uses a bootloader to make things work more smoothly with USB serial, but as I found out it is not necessary to use a booloader to run Arduino programs (or “sketches” as they are called).
The ability to run without a bootloader turned out to be key since there is no Arduino bootloader that works as-is with the Atmega48 chip. Although I’ve seen in the forums that others have hacked it to work with some simple changes to the code, I decided to go without it, and in hindsight I’m glad I did since it would have been a lot of extra effort to compile a custom version of the bootloader, and since the 48 chip only has 4k of flash, the bootloader would have taken up valuable storage space (the Arduino runtime takes quite a bit of that space – a simple LED blinking program consumes about 2.5k).
The only hardware required to get things working was the Atmega chip itself, a parallel printer cable and some 1k resistors. Really, that is it. The Atmega chip has an onboard oscillator so no crystal is necessary at all and no other hardware is actually required to program the chip, and the programs are self-contained, so they can be uploaded to the chip using the parallel port. In most of the examples out there on the net, the parallel programmer is only used to get the bootloader onto the device, but the same technique can be used to upload the actual code as well.
I soldered a cable up using a DB25 connector that I had lying around, but for many of you it might be easier to take a regular parallel printer cable and just cut the printer end off and strip the needed wires at the end. I used this pinout for my cable, and the avrdude programmer utility to program the chip. I was using Ubuntu Linux, so avrdude was available using apt-get:

# apt-get install avrdude

Once the cable was plugged into the parallel port (I’m using an old laptop for this, I think it will work with USB parallel port converters too, but I haven’t tried it) I used the following command to check connectivity to the Atmega chip:

# avrdude -p m48 -c bsd

Note that this has to be run as root or some user that has access to /dev/parport0. Running this command should give you the chip configuration (the fuse settings):

avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.00s

avrdude: Device signature = 0x1e9205

avrdude: safemode: Fuses OK

avrdude done.  Thank you.

This was the first step. The next step is to compile .hex files that can be uploaded to the chip. The easiest way to do this is with the Arduino IDE. I’ll cover that in the next post since there was some configuration necessary to add the Atmega48 as a target device.
