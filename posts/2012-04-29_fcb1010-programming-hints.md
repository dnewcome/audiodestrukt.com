---
title: "FCB1010 programming hints"
date: 2012-04-29T01:27:19-08:00
url: https://audiodestrukt.wordpress.com/2012/04/29/fcb1010-programming-hints/
id: 243
categories: Uncategorized
tags: Live PA
---

# FCB1010 programming hints

I just wanted to share a few thoughts now that I’ve gone through and programmed the first bank of presets on my new FCB.
One of the things that I wanted to do with my foot controller was to play bass lines using my feet. I figured since the switch layout of the FCB was staggered, more or less like a piano keyboard, that this would be a natural thing to do with it.
If you saw my last post you’d know that nothing about this pedal board has been what I was expecting. Getting this initial bank set up was no exception.
From the factory, every preset sends a Midi program change message and has the 2 expression pedals activated. I wanted my patches to send just a note event and not a program change so for each of the presets I set up I disabled the PC message and added the note message. I left the expression pedals set up as they were. As a side note, having the expression pedals part of the patch configuration is kind of a pain in this case since if I ever want to send a different CC message I have to go through each of the presets and change it individually. There is also the possibility that one of the presets will get accidentally configured to send the wrong CC message for the expression pedals.
Ok so what I want to go into here is the basic concept behind programming this thing. The manual give you these excruciating step-by-step instructions for the different types of messages but never explains the overall concept behind programming the thing. Of course, you would figure it out after you’d gone through the process a few times, but for those of you that are thinking about buying one of these and don’t have one in front of you my explanation could be pretty helpful in grokking just what this thing is all about.
There are really only two modes that the pedal board can be in — patch select or edit mode. There are two different patch select modes, but that doesn’t matter for our discussion here. If the pedal is in patch select mode there is an active or currently selected patch. When we enter edit mode, this is the patch that we will be editing.
Edit mode is entered by holding down the “down” foot switch for 2.5 seconds. In edit mode, the very first “screen” is the external switch jack configuration. This is not part of my setup, and unless you are controlling a guitar amp that has a channel selector switch that you want to use, you’ll skip this configuration step every time. Hitting the “up” foot switch will put us into the main pedal configuration step. In this step the LED above each switch will be solid on or off depending on whether that particular function is enabled. Holding the switch down will turn the function on or off. Hitting the switch again enters the configuration step for that function.
Reading back up through this description is making me think that I’m not explaining this stuff much better than the manual. The main thing to understand is that once the main configuration step is reached, the LEDs give you a bird’s-eye view of what is configured for that preset. All of the labels on the switches should make a lot more sense when you think of things this way.
In order to get my Midi keyboard bank working, I went through the first 10 presets and disabled the PC message and added a note message corresponding to the note that I wanted to send. I started with note F3 for the first foot switch. One thing to notice is that the Midi note function is designed to also send a CC message along with the note-on message sometimes. In my tests this message gets sent irregularly, and on note-off rather than note-on like the manual suggests. This may be a firmware bug that is fixed in the UnO firmware, but I’m not sure. In any case it is relatively harmless, but is annoying to me nonetheless.
