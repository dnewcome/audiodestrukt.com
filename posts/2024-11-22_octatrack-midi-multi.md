---
title: "Octatrack MIDI multi"
date: 2024-11-22T00:32:04-08:00
url: https://audiodestrukt.wordpress.com/2024/11/22/octatrack-midi-multi/
id: 1506
categories: Uncategorized
tags: audio, MIDI, music, music-production, reviews
---

# Octatrack MIDI multi

I’m still jamming on my Octatrack today. I hooked up my Waldorf Blofeld to the mix. Same kind of setup where I have MIDI going out of the OT and into the Blofeld.

I chose the Blofeld for this experiment because it’s 16 part multitimbral and I can trigger a few different sounds at once from different tracks on the OT.

So some things to note about the OT and MIDI. By default all of the audio triggers also send corresponding MIDI notes out. This can be a problem when trying to work with external devices because tracks that are just intended to play samples will be triggering external sounds simultaneously. In the project MIDI configuration we can set Audio MIDI tracks to INT so that notes triggered by audio tracks don’t send anything outside the OT.

Once we have that set up, we can create a few MIDI tracks with output channels set (this is one time that the click switch in the buttons is important – making changes to the MIDI track on a channel while in MIDI mode requires a click of the knob to take effect.

I went into track settings and set the first two tracks to ‘plays free’ and trigger mode hold so you have to hold the button down to keep the track playing. I set the quantize mode to 1/16 since I’m pretty sure I can push multiple buttons down at least with that margin of error.

Clicking in a few trigs in record mode on the first two tracks set them up with a few notes to play as arpeggiators. Note that if the transport is not playing the quantization settings don’t come into play. It’s effectively the same as immediate mode in the track settings window (where we set the tracks to “plays free” earlier).

Now with the transport running the tracks are synced to play within 1/16 (one step) from each other. And we can jam around pressing the buttons before or after one another in varying timings in order to get the tracks running together in different ways. It’s a very cool way to jam on some sequences.

I do wish that the MIDI track arpeggiator worked with internally triggered notes. It seems to only affect incoming MIDI notes from external controllers. There might be a way to get this to work but I haven’t found it yet.
