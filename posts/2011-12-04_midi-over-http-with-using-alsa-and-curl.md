---
title: "MIDI over HTTP with using ALSA and Curl"
date: 2011-12-04T17:31:30-08:00
url: https://audiodestrukt.wordpress.com/2011/12/04/midi-over-http-with-using-alsa-and-curl/
id: 98
categories: Uncategorized
tags: 
---

# MIDI over HTTP with using ALSA and Curl

A few weeks ago, I created a small Node app called Dub Siren to demonstrate playing audio under Node using SDL. My plan was to expand the idea into a more fully-featured sampler. One of the things that I wanted to check out was the audio latency between the time a request was initiated and the time that the sound was played.
In order to get a feel for whether the latency was musically tolerable, I decided to rig up my Korg NanoPad so that I could send HTTP requests to the Dub Siren app. I realize that this is a completely unscientific way of measuring the latency, but it mirrors the use case that I care about most, and that is the live realtime performance of the app.
I hacked the MIDI-to-HTTP script up in bash using curl. I’m using Ubuntu, which means that the standard MIDI interface is ALSA. I didn’t want to mess with ALSA-OSS compatibility, although that should have let me treat the MIDI controller like a regular file (I think). However, ALSA has a few useful tools for getting MIDI data to standard out. Amidi lets us monitor a connected MIDI device for data. I want to take this data and send it to the Dub Siren app using curl. In order to do this we need to invoke curl for each line of output that we get from amidi. Fortunately the common UNIX xargs tool will let us do just this.
To start with, I connected my NanoPad using USB and used amidi to find out the hardware device number that it had been assigned:

$ amidi -l
Dir Device    Name
IO  hw:1,0,0  nanoPAD MIDI 1

Here you can see that the device number is 

hw:1,0,0

Now we can use this device number to monitor the device, again using amidi:

$ amidi -d -p hw:1,0,0

90 26 7F
80 26 40

The data shown is a single pad hit. All values are shown in hexadecimal. 0x90 is the MIDI command for a note-on, and 0x80 is the command for a note-off. The second number, 0x26 is the note number for the pad that I pressed. The third value is the velocity number. 
Data is output to the console continuously until the process is killed. What I need to have happen is for curl to be invoked for each line of this continuous output. This would be tricky since without some help from xargs. Xargs is intended to do things like run a command for each file found by find or to take a list of arguments and put them all on the same line. In short, it processes input and calls a target command with the input as the arguments.
Here is the command 

amidi -d -p hw:1,0,0 | xargs -I {} ./midicurl.sh {}

Where midicurl.sh is a wrapper around curl that parses the arguments and makes the HTTP request:

tokens=( $1 )
## since this is a drum sampler for now, we only care about note-on events
if [ ${tokens[0]} == "90" ] ; then 
	echo $1
	curl "http://localhost:3003/play?note=${tokens[1]}&vel=${tokens[2]}"
fi

I filter out note-off events by checking for MIDI command 90. The only interesting thing here is that all of the arguments get passed from xargs in one string and we have to tokenize them. There should be a way to get xargs to pass them as separate arguments, but I didn’t seem straightforward and I didn’t have the time to figure it out.
Now hitting a note on my NanoPad results in an HTTP request to the Dub Siren’s /play method, passing note number and velocity in the query string. Pretty cool.
However, the latency is pretty unusable. It is probably ok for the actual siren sample, but not for drum samples. It’s way too slow to play a drum beat live on the pads. What to do? Well, since we are using Node, there is another way to easily pass data that eliminates the overhead of HTTP. That is Websockets.
I’ll show the code for using Websockets via Socket.IO in the next post.
