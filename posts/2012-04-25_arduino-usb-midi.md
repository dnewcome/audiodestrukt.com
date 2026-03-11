---
title: "Arduino USB Midi"
date: 2012-04-25T22:54:35-08:00
url: https://audiodestrukt.wordpress.com/2012/04/25/arduino-usb-midi/
id: 216
categories: Uncategorized
tags: 
---

# Arduino USB Midi

As I’ve mentioned previously, I’m working on a new foot controller concept (which I’ll reveal soon). As part of my initial research I thought it would be pretty awesome if there was some way to get my controller to show up natively as a USB Midi device instead of using Firmata or some other serial interface which would require running Max/MSP or PD to convert the data to Midi messages.
It turns out that since the Arduino UNO uses a programmable MCU to perform USB serial, it is possible to reprogram the firmware to provide a USB audio device class to the host OS.
Darran Hunt has done all of the hard work here by hacking up a firmware that does Midi over USB and lets us put data over the wire using the Arduino serial communications API. You can find that code here.
The important thing to notice is that this is not the same as the Arduino bootloader and it does not get written to the main AVR chip on the board. It is code for the Atmega8U2 that drives the USB port on the Arduino board. In order to flash this chip, we have to put the board into DFU (Device firmware update) mode
I used dfu-programmer on Linux to flash the new firmware to my Uno. Installing the tool was easy using apt-get:

$ sudo apt-get install dfu-programmer

Here is the command to flash the Midi firmware (hex file) using DFH:

$ dfh-programmer at90usb82 flash Arduino-usbmidi-0.1.hex

Once the firmware has been flashed, you can no longer use the normal bootloader to program the Arduino! I get around this by using a homemade serial programmer. I’ll post this later, but if you have a programmer that can connect to the 6-pin ICSP header on the board you should be good to go.
To test things out I flashed an Atmega48 chip out-of-circuit with the test program provided by Darran. I swapped the chips in my arduino and plugged it in. Here is how the device shows up in Linux:

$ amidi -l
Dir Device    Name
IO  hw:1,0,0  Arduino MIDI MIDI 1

And then to test that the demo program is sending midi data:

dan@dan-Latitude-D600:/tmp/build1002454732081805362.tmp$ amidi --dump -p hw:1,0,0

So far, things are looking pretty good. I’ll post some new stuff using this firmware in a little while.
