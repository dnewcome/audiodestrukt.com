---
title: "State of open-source vinyl control"
date: 2013-01-30T14:14:48-08:00
url: https://audiodestrukt.wordpress.com/2013/01/30/state-of-open-source-vinyl-control/
id: 557
categories: Uncategorized
tags: 
---

# State of open-source vinyl control

I’ve taken another look at a few open-source DJ programs recently as a result of another audio hacker’s Mixxx plugin project. The venerable openjay.org seems to have been shut down now that Mixxx is a mature project, so I’m not sure where the definitive source for news is anymore in this space.
I’ve been following DJ software on and off for a while and one of the things that I want to be able to do is use my Traktor timecode vinyls for control.
When I looked at this space the last there was an open source project to read these timecode vinyls called libxwax, which part of a host application called Xwax. I sort of got xwax working with my vinyls but for some reason I couldn’t get things working reliably enough. I’d get skips or lose sync for some reason and I never figured out what was going on. 
I also tried Mixxx around that time. Mixxx also supports timecode vinyls via libxwax. I got better results with Mixxx and it was a lot more intuitive to use, however I kept getting crashes, at least with the Windows build, so I shelved things and just used a demo version of Traktor Scratch to play around. I still wanted something open-source though. 
After seeing Mixxx again I gave it another shot on my Retina Mac. I plugged my turntable into a cheap Behringer UCA202 USB audio interface and configured vinyl control in Mixxx. To my surprise things work very well now! I had to do a few things to get it to read the timecode first, but once I got it set up it was pretty solid.
Here are my settings. Note that I had to turn the preamp up a little bit to get anything working. Without the preamp, I would occasionally get a little slow movement on the track, which was a little confusing. It’s hard to tell what’s going wrong, so turn the preamp up a little bit if things don’t seem to be working.

I turned on skip prevention, which seems to be necessary for scratching. Even with my tone arm weight set pretty heavy I was still getting skips without it.
