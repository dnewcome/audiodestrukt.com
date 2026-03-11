---
title: "Local network audio"
date: 2011-10-30T13:48:46-08:00
url: https://audiodestrukt.wordpress.com/2011/10/30/local-network-audio/
id: 56
categories: Uncategorized
tags: 
---

# Local network audio

I have been looking around at setting up a JamLAN (I think I just made that up) that could be used to implement a software-based JamHub. I figured that there would be plenty of ways to get this working on a local network (as opposed to over the Internet), but I was kind of disappointed. 
The basic requirements are:

Platform independence (Win/Mac/Linux)
Relatively low latency (10-20ms)
Handle full-mesh between 4 stations (volume of each peer adjustable separately)

Things that would be nice:
Ability to dynamically reconfigure who is connected. For example a singer leaving one jam and entering another.
Ability for one performer to perform with two separate groups simultaneously. For example, a singer riffing on two different songs or a drummer leading two different blues jams at the same time. This could be pretty wild.
Possible solutions:
So there are four different approaches that I thought of:

NAS (Network Audio Server)
PulseAudio
Jack
PD (using netsend~ and netreceive~)

So far I have struck out on all counts. 
NAS doesn’t seem to support anything besides point-to point audio, and I’m not able to figure out how to get more than one connection working. It seems to be mostly designed for X11-style remote connection of a single audio device much like an X server takes over a display device. 
PulseAudio seems like it could have worked but RTP doesn’t work in the Windows build that I had, which would have been necessary to get a connection fanout of > 1 I think. PulseAudio supports virtual connections called tunnels, but it wasn’t clear if that would allow multicasting of the streams. 
Jack seemed promising until I realized that it was mostly intended to allow master/slave type of distributed audio for the purposes of offloading CPU-intensive audio effects rather than allowing multiple sets of audio hardware on the network. Also there are no fewer than 3 network audio protocols under Jack, all of them being incompatible, and all having slightly different capabilities. 
I thought that PD would be the stupid-simple way to finally get this working, but unfortunately netsend~ is quite dusty these days. It didn’t build cleanly for me under linux until I patched it for an antiquated use of gethostbyname(). Even then I had compiler warnings. This didn’t inspire confidence. On the Windows end, I needed an old version of libpthread on order for netsend to load. After all that, making connections between the two machines crashed the windows netreceive~ consistently, after repeated attempts to connect resulted in gibberish data including negative channel counts and random buffer sizes/byte counts.
So this leaves me back at square one. I’d like to be able to get a simple network audio setup going that could accommodate 4 full-duplex audio streams. Doesn’t sound like a lot to ask. Maybe I should be looking at VOIP stuff like Asterisk. I also thought about using ShoutCast DNAS, but I thought it might be kind of odd to have to run multiple audio apps to receive the individual streams.
