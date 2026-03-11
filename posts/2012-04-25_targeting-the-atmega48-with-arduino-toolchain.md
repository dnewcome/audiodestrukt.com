---
title: "Targeting the Atmega48 with Arduino toolchain"
date: 2012-04-25T22:19:19-08:00
url: https://audiodestrukt.wordpress.com/2012/04/25/targeting-the-atmega48-with-arduino-toolchain/
id: 213
categories: Uncategorized
tags: 
---

# Targeting the Atmega48 with Arduino toolchain

I’ve been prepping for a new foot controller project that I’m using the Arduino on. I had a few small things that I wanted to note here since It seems that I haven’t written a lot of this stuff up.

It so happens that I have a bunch of Atmel AVR Atmega48 microcontroller chips lying around. I have the official Arduino UNO board also, which shipped with the Atmega328. It turns out that the 48 works perfectly well with Arduino, but there are a few things to keep in mind to get things working.

First off, there is no bootloader for this device. If you are using an UNO though, the bootloader is actually in the smaller ATmega8U2 chip anyway, so this isn’t an issue. 

The Arduino IDE doesn’t have a board configuration for the 48, so in order to get it to build hex files that will work, we have to do a little configuration.

We need to modify a file called boards.txt. On Linux this is installed here:

```

/usr/share/arduino/hardware/arduino

```
I added a new section for the Atmega48 like this:

```

atmega48.name=ATmega48

atmega48.upload.protocol=avrisp
atmega48.upload.maximum_size=4094
atmega48.upload.speed=38400
atmega48.upload.using=parallel

atmega48.bootloader.low_fuses=0xe2
atmega48.bootloader.high_fuses=0xdf
atmega48.bootloader.extended_fuses=0xff
atmega48.bootloader.path=atmega
atmega48.bootloader.file=ATmega48.hex
atmega48.bootloader.unlock_bits=0x3F
atmega48.bootloader.lock_bits=0x0F

atmega48.build.mcu=atmega48
atmega48.build.f_cpu=16000000L
atmega48.build.core=arduino

```
I’m not sure all of these things are necessary. The most important thing is to get the memory size correct. I’m not sure that 4094 is completely correct. It would make more sense to try 4096 there (4k) but I haven’t tested that out.

I’m posting this up here for my own reference, and as I tweak it I’ll post more details. I have run into some issues with clock speeds and the like. For my low-cost Arduino clone using the 48 chip I used its internal oscillator, which is running at half the speed of the normally clocked Arduino. Because of this, some sketches like the servo motor sketch will not work correctly. I have a hunch that setting f_cpu correctly should alleviate this but I have not tried it.

Hopefully if you have some of these chips sitting around you can get them working in your Arduino too.
