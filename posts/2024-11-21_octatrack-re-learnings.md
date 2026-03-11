---
title: "Octatrack re-learnings"
date: 2024-11-21T18:17:36-08:00
url: https://audiodestrukt.wordpress.com/2024/11/21/octatrack-re-learnings/
id: 1486
categories: Uncategorized
tags: elektron, music, octatrack, technology
---

# Octatrack re-learnings

I’m digging back into using my Octatrack and I’m finding that I have to re-learn a bunch of things about how it works. Saying that it’s a quirky machine is an understatement. There are some guides like Merlin’s OT manual that go into the philosophy of the machine, but I’m writing things here with my own live use in mind.

I used to think of the OT as a looper. Then I thought of it as a sampler. Then I thought of it as a sequencer. Now I think of it as a performance recorder – sort of.

Using the OT as a recorder means setting up the recording machines according to the inputs you have connected. This is pretty straightforward but there are some nuances that make it a little weird. The first is that you can’t hear anything you are recording by default until you are playing it back. That is, monitoring is disabled by default. 

There are two ways to fix this. The first is to go to the mixer page and enable direct monitoring. There is a confusingly named knob called “DIR” that sets the direct input level that will be passed through the machine. The second way is using a THRU track. I won’t get into that here but I think that most people that are proficient at the OT have a THRU track somewhere in their setup, sometimes the last track (if they aren’t using it as a master track, which is a whole other thing).

Once we have monitoring out of the way there are trigger modes for enabling recording. The recorder can be enabled using a special track of triggers on the pattern (separate from the normal trigs that control playback or the trigs that control swing and slide for that matter). These can be edited separately using FUNC+BANK.

I’m not going to cover trigs here. I’m going to focus on manually recording things. There are three little buttons at the top left of the machine next to the (confusing) headphone volume knob. These three buttons trigger recording manually. There are a few modes. One mode just sets the thing off recording into the wild blue yonder. The default recording length is really long (MAX) unless you set it to some number of trig steps. I like to either set the max length to one bar or use the momentary mode where you have to keep the button held down for as long as the recording lasts.

There are some tricks for recording to different tracks that I learned here https://www.youtube.com/watch?v=lniCqGfqBy4

One of which is that you can hold the track button T1, T2 etc and hit the record button to trigger that track’s recorder. There are some others too, you should watch his video.

Other things to note are that you can record while in the sample editor which lets you see the waveform as it’s being recorded which is totally awesome and I didn’t know you could do. Hit AED and then start the recorder and you should see it recording. Then you are already in the editor and you can trigger playback using FUNC+YES (another counter-intuitive trick that works in a lot of places like previewing slots).

Speaking of slots, I also forget about how this works. Slots are not slices. Slices are not slots. They are separate. Slices are populated from the slicer and slots are loaded manually in the machines (FLEX or STATIC). Note that there are two separate banks of slots that are shared by FLEX and STATIC respectively. So loading a slot in a FLEX machine will load that same sample in all FLEX machines. Same with STATIC. So there are a total of 256 possible slots that can be loaded and they are split between STATIC and FLEX machines separately.

Confusingly, slices are not shared between machines. A FLEX machine that contains a sliced waveform will have separate slices than another FLEX machine. I think this is because the main sample that is loaded in a FLEX machine is separate from slots (you can play slots and the main sample separately on any FLEX machine but just not at the same time since each track is monophonic).

Another confusing thing is that loop is enabled by default on FLEX machines, so any short sample that is played like a kick drum in a slot will loop indefinitely until another trig happens on the same track. This can be turned off in a settings page for the machine https://www.elektronauts.com/t/slices-looping-on-trigger-disable/151650/2

Ok that covers some main things that I had to re-learn just now. Hope this helps you if you read this far.
