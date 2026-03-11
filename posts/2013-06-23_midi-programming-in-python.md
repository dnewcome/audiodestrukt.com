---
title: "Midi programming in Python"
date: 2013-06-23T23:21:51-08:00
url: https://audiodestrukt.wordpress.com/2013/06/23/midi-programming-in-python/
id: 750
categories: Uncategorized
tags: 
---

# Midi programming in Python

I’ve been playing with different ways to script MIDI I/O over the last year or so. There are a ton of different ways to skin this cat including special-purpose languages like PD and KeyKit. However, it’s nice to be able to do some coding in a more general purpose language if for no other reason that other programmers can see what the hell you’re trying to do without wrapping their head around some bizarre environment.
What I’ve found is that for the most part, MIDI has been relegated to game libraries and low-level libraries like PortMidi and RtMidi. Some of these libraries are also kind of old and rely on outdated midi device interfaces (OSS, etc.).
The game libraries (pygame, rubygame) make things relatively easy to get started, but I’m not a huge fan of dealing with things in a framerate-based environment. Also if you aren’t careful, your midi program will consume 100% of your cpu like a badly-written game.
I’m spinning up on python for a new gig, so I figured I’d try out pygame instead of rubygame like I did last time. I started with some kind of hello world app. I’m on OSX so I had some issues with fonts in the test apps that I dug up around the Web.
To get pygame installed I first installed SDL using homebrew:
# brew install sdl
Then I installed pygame using pip:
# pip install hg+http://bitbucket.org/pygame/pygame
Note that I installed directly from bitbucket, due to an error in the build that has been fixed in the latest sources.
The pygame MIDI docs, along with some sample pygame code got me as far as reading my Korg NanoPad and dumping the MIDI events to the console. Here is the code:

import sys, pygame, pygame.midi

 # set up pygame
 pygame.init()
 pygame.midi.init()

 # list all midi devices
 for x in range( 0, pygame.midi.get_count() ):
     print pygame.midi.get_device_info(x)

 # open a specific midi device
 inp = pygame.midi.Input(2)

 # run the event loop
 while True:
     if inp.poll():
         # no way to find number of messages in queue
         # so we just specify a high max value
         print inp.read(1000)

     # wait 10ms - this is arbitrary, but wait(0) still resulted
     # in 100% cpu utilization
     pygame.time.wait(10)

The output of the above looks something like this after starting up and hitting a pad on my NanoPad controller:

'CoreMIDI', 'IAC Driver Bus 1', 1, 0, 0)
('CoreMIDI', 'IAC Driver IAC Bus 2', 1, 0, 0)
('CoreMIDI', 'nanoPAD PAD', 1, 0, 0)
('CoreMIDI', 'IAC Driver Bus 1', 0, 1, 0)
('CoreMIDI', 'IAC Driver IAC Bus 2', 0, 1, 0)
('CoreMIDI', 'nanoPAD CTRL', 0, 1, 0)
[[[144, 55, 107, 0], 4993]]
[[[128, 55, 64, 0], 5059]]

I’ve enumerated the MIDI input and output devices in the code, and the first 3 items in the list above are the inputs and the rest are the outputs. You can see the MIDI data in the two python lists at the end.
When I hit ctrl-c to stop the program I get an error from PortMidi. This probably isn’t a big deal, but I suppose exiting the program should be handled more gracefully and/or this exception should be handled. Not sure what they pythonic/pygameic way of doing this is yet, but here is the trace:

Traceback (most recent call last):
  File "midi.py", line 21, in <module>
    pygame.time.wait(10)
KeyboardInterrupt
Exception Exception: Exception("PortMidi: `Bad pointer'",) in <pypm.Input object at 0x1038f3df0> ignored

I came across some interesting code in the course of getting this stuff working. There is apparently a pygame event type MIDI that can be consumed just like a mouse move or keypress event. However it looks like we still need to pull the data using read() anyway, so I’m not sure if this is useful.
