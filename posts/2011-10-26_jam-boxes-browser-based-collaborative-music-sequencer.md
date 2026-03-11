---
title: "Jam Boxes &#8211; browser-based collaborative music sequencer"
date: 2011-10-26T02:22:27-08:00
url: https://audiodestrukt.wordpress.com/2011/10/26/jam-boxes-browser-based-collaborative-music-sequencer/
id: 24
categories: Uncategorized
tags: 
---

# Jam Boxes &#8211; browser-based collaborative music sequencer

I competed in the recent NodeJS Knockout competition with Shane Tomlinson and Jeremy Flores, producing Jam Boxes, the awesome multi-user music sequencer. It turns out that the winning team also built an audio sequencer application, so I think we had the right idea even though we finished in the middle of the pack.
I met Jeremy through the Hacker Dojo audiohackers meetup, and Shane is a good friend from college that worked with me on my first startup, Ubernote. The team came together when Jeremy approached me after the audio hacking meetup and started asking me about my Javascript experience. He asked if I was doing Node Knockout, and told him that I tried to get one of the 200 team spots, but they were all gone by the time I tried to sign up!
To make a long story short, Jeremy had the spot but didn’t have much experience with Node.js and I had experience but no spot. I wanted to make this a dream team so I convinced Shane to join us as the resident Javascript guru. Born of the Dojo Audio and Music hacking meetup, of course we had to do a music application. Jeremy had the basic idea from a prototype iPhone app that he built some time ago.
The UI was done using Raphael.js, the audio engine is a mix of dsp.js and audiolib.js. It only works on Firefox since we didn’t have time to get the audiolib.js ring buffer fully working, so we had to roll our own. Multi-user data synchronization is courtesy of Socket.io. We knocked this thing out in probably 36 hours since we actually went home and slept both nights!
Go check it out here.
