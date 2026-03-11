---
title: "State of Audio and Midi APIs"
date: 2024-03-11T08:32:08-08:00
url: https://audiodestrukt.wordpress.com/2024/03/11/state-of-audio-and-midi-apis/
id: 1198
categories: Uncategorized
tags: 
---

# State of Audio and Midi APIs

I know this is a very general title, but I want to write up a few things about my latest dive into music programming libraries. Every once in a while I get the bug to write a few little utilities for doing audio and midi work and it seems like every time I look I find different things out there. Some that I have used  in the past are now very old and unmaintained so it’s helpful to poke around the internet pretty much every time I get back into this.

For audio, I used node.js to write some audio server things years ago using node_SDL. Years ago it seemed like game libraries were the best bet for doing realtime audio programming. That seems to have changed somewhat over the years though.

I’m thinking about two different projects – one that is a sort of MIDI arpeggiator and one that is a headless mixer/sampler thing. 

For audio I got python-rtmixer working on my Ubuntu 23.10 workstation. It took a little fiddling around to get sounddevice doing the right thing. I had to reboot after removing some pulseaudio things that were installed. Also I was getting confused between pulseaudio and portaudio for some reason. Ooops, that cost me a little time.

The sounddevice library includes a way to list the devices on the shell, so that was a very helpful thing to do to get the device numbers on my system as well as confirm that portaudio was working correctly.

(py) ➜  examples git:(master) ✗ python -m sounddevice<  0 HDA Intel HDMI: VS278 (hw:0,3), ALSA (0 in, 2 out)   1 HDA Intel HDMI: 1 (hw:0,7), ALSA (0 in, 8 out)   2 HDA Intel HDMI: 2 (hw:0,8), ALSA (0 in, 8 out)>  3 Loopback: PCM (hw:1,0), ALSA (32 in, 32 out)   4 Loopback: PCM (hw:1,1), ALSA (32 in, 32 out)   5 HDA Intel PCH: ALC887-VD Analog (hw:2,0), ALSA (2 in, 2 out)   6 HDA Intel PCH: ALC887-VD Alt Analog (hw:2,2), ALSA (2 in, 0 out)   7 Logitech BRIO: USB Audio (hw:3,0), ALSA (2 in, 0 out)   8 R24: USB Audio (hw:4,0), ALSA (8 in, 2 out)   9 hdmi, ALSA (0 in, 2 out)  10 pipewire, ALSA (64 in, 64 out)  11 pulse, ALSA (32 in, 32 out)

Once I knew which device number I wanted to use I could plug that in here for example.

(py) ➜  examples git:(master) ✗ python signal_processing.py 
  input latency: 0.008
 output latency: 0.008
            sum: 0.016
       DSP size: 4096
=== Start Processing
^C
=== Interrupted by User
  recorded blocks: 1014 (min/max size: 128/128)
    played blocks: 1014 (min/max size: 128/128)
        DSP calls: 30
 input underflows: 0
 input  overflows: 0
output underflows: 0
output  overflows: 0

I installed portaudio19-dev to get portaudio on my system. I tried pyaudiomixer and never got it to compile due to some issues with numpy . There are some incompatibilities with cython from what I can tell and I didn’t spend enough time on it to get it working. I also played with pymixconsole but it turns out that this is not a realtime mixer but a batch mixer. It might be interesting to play around with this to make complete tracks with.

There is a portaudio wrapper for node that I hadn’t seen before as well `https://github.com/Streampunk/naudiodon

I couldn’t get this to install from npm due to python version issues and gyp. I downgraded my node to v15 but there were still some issues. 

I was able to build it from source though using node-gyp-build. To be continued in part 2.
