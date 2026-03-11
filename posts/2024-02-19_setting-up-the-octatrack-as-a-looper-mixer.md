---
title: "Setting up the Octatrack as a looper/mixer"
date: 2024-02-19T11:05:30-08:00
url: https://audiodestrukt.wordpress.com/2024/02/19/setting-up-the-octatrack-as-a-looper-mixer/
id: 1107
categories: Uncategorized
tags: 
---

# Setting up the Octatrack as a looper/mixer

I’m messing around with my synth gear again in the new year. I recently traveled with the OP-Z and that got me thinking about the workflow of the Syntakt. So I dug the Syntakt out and jammed around with it for a while. I’m starting to get pretty quick with the Elektron workflow so I thought I’d revisit my Octatrack. 

I got along ok with the Octatrack after I figured out the basic idea of how it works and some of its quirks. I spent time re-learning and figuring things out again. It’s not like riding a bicycle. I had to look a lot of stuff up again even after getting familiar with the Syntakt. I get the feeling that Elektron is ripe for releasing a new Octatrack soon with some of the advancements made in the Digitakt/Digitone/Syntakt boxes. The OT seems a little clunky now in comparison. It’s hard to put your finger on it but there are just some things that seem more intuitive on the newer boxes.

Anyway back to the OT. I wanted to set up the OT alongside the Syntakt so that I could grab loops from the Syntakt and mix using the crossfader with other patterns. Someone needs to make a groovebox that can play simultaneous patterns and mix between them. I’ll have to look back again at the “megamix” function that the Roland MC-505 had. I think you could take elements from another pattern and play along with the current pattern. I’m not sure if it let you fade the levels or not though.

In order to do this I set up the left tracks (1-4) as “deck A” and the right tracks (5-8) as “deck B”. I used the crossfader scenes to lock the volume parameter as min/max on either side. I set up tracks 1 and 2 with a Thru and a Flex machine respectively. I did the same for tracks 5 and 6 on the right hand side.

I set the headphones up to only play the cue buss. This is a personal preference as I can always hear the mains and I don’t want to get confused about what I can hear vs what the audience is hearing.

I set up the flex tracks with a one-shot record trig at the beginning of the pattern and a note trig to start the loop also at the beginning. What this will do is allow you to hit “yes+track” to enable the one-shot trig and start recording a loop in time. This will capture 4 bars (in my case, I set the pattern length to 64 steps) perfectly in time and start playing the track back immediately.

The next part of this workflow revolves around muting, cueing and the crossfader. With one single device connected you are basically just bouncing back and forth between live input on the left and recorded audio on the right. So the second Thru track isn’t strictly necessary, however it’s nice to have a symmetrical setup that will work with another device also. I have tried this out with the Syntakt on the left (deck a) and the Synthstrom on the right (deck b). 

This allows several scenarios:

1) Mixing between live sources. Enable both Thru tracks (1 and 5) and mute all others. Play both audio sources in time with midi sync (I forgot to explicitly mention that I’m using the OT as the clock source and sending midi transport and sync to the other devices). Move the fader back and forth to mix just like a DJ mixer.

2) Going from live source to recorded loop and back to the same live source. This entails using the flex machine on deck b (right side) to record a loop from the live source. Hitting “yes+track5” button will enable the record trig and once the trig is hit and the loop plays through it will start playing back. Since the fader is on the left it won’t be audible in the main outputs but you can cue it to listen and check in the headphones with “cue+track5”. If it sounds like it’s looping correctly we can make sure it’s not muted and move the fader to the right. Make sure nothing else is live. We want other things to be muted on deck b here. If all goes well it won’t sound any different. We are just playing a loop of what we were listening to live. I’ve noticed that it takes some tweaking to get the levels to match up. I set the input of the Thru track to +64 which is the maximum. It seems like this is the nominal level that the recorder records at despite it seeming like zero level should match it. I’ts a quirk of the Octatrack apparently. Also the fader curve isn’t really linear and the sound at the middle of the fader seems to dip even with the same source playing on both sides. So my recommendation is to move the fader a little at first to test the waters, then just flip it all the way over quickly, avoiding staying in the middle longer than necessary.

Once we have a loop playing we can change the pattern on deck a or do whatever we want. It’s best to leave the transport playing though, otherwise we have to get the timing right again by hitting play on the beat and using the right and left arrows to nudge. Effectively beat matching. Depending on the pattern that is playing this might be easy or very difficult. I’ts better to leave the transport in play if possible. We can also mess with effects or duplicate the track and filter it or all sorts of other things. We can record another loop with just the high-hats or whatever.

Once we are finished messing around with samples and effects or changing patterns, it’s time to go back to deck a. As long as something is playing in time on the deck (check in the headphones by cueing track 1) we can just move the fader back to the left to start getting live input from deck A. Now we are back at the beginning. Jam around on the Syntakt, rinse and repeat.

3) The third option is just a mix of the first two. Now that we have multiple live sources we can record loops from either one. In this case it’s less clear what the desired workflow should be with respect to the fader. Recording loops from deck a on the deck b side would allow kind of a megamix element where we can bring in parts of what is playing on deck a with effects and vice versa. Recording loops on the same side as the deck could be something done to bring in a “preview” mix before fully committing to what’s live on that deck. 

The possibilities are many here. I’m going to be jamming with this setup a little bit and I will try to document what I find.
