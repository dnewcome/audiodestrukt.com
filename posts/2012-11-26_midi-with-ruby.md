---
title: "MIDI with Ruby"
date: 2012-11-26T00:35:31-08:00
url: https://audiodestrukt.wordpress.com/2012/11/26/midi-with-ruby/
id: 463
categories: Uncategorized
tags: 
---

# MIDI with Ruby

I was disappointed with not being able to use Pure Data on Windows to send the appropriate MIDI sysex message out to change the operating mode of my APC20 when I was doing this [text scroller patch](http://www.youtube.com/watch?v=iqPqP-IRhFA). For some reason when I sent the sysex start and end bytes (0xF0 and 0xF7) messages to the APC it gave me an error. I could send these messages to my MIDI Yoke outputs, but I wasn’t able to get MIDI-OX to pass sysex from the Yoke to the APC for some reason. Long story, but it didn’t work out like I had hoped.

I looked into finding some utilities to send sysex and I didn’t find anything from this decade that actually worked on 64bit Windows. It’s possible that I could have gotten MIDI-OX to send a sysex file using [VBS scripting](http://www.midiox.com/cgi-bin/yabb/YaBB.pl?board=MOXScript) but I just didn’t want to go there. 

I thought I’d be able to write a Ruby or Perl one-liner to send the proper sysex command out, and I was mostly right, but it turned out to be harder than I thought to find a decent MIDI library that was reasonably recent.

I ended up going with [Unimidi](http://tx81z.blogspot.com/2011/06/unimidi-platform-independent-realtime.html), which turned out to be pretty awesome. 

Here is a little code snippet that sends APC20 sysex messages to change its operating modes. Ruby isn’t my main language so be kind.

```

require 'rubygems'
require 'unimidi'

output = UniMIDI::Output.open(:first)
output.open do |output|
 mode = ARGV[0]

 if mode == "ableton"
 output.puts(0xF0, 0x47, 0x7F, 0x7B, 0x60, 0x00, 0x04, 0x41, 0x08, 0x02, 0x01, 0xF7)
 else
 output.puts(0xF0, 0x47, 0x7F, 0x7B, 0x60, 0x00, 0x04, 0x40, 0x08, 0x02, 0x01, 0xF7)
 end
end

```
