---
title: "Slicer Plugins"
date: 2024-01-31T22:02:23-08:00
url: https://audiodestrukt.wordpress.com/2024/01/31/slicer-plugins/
id: 1045
categories: Uncategorized
tags: 
---

# Slicer Plugins

Long ago I was a Drum and Bass producer. I used FL Studio (then Fruityloops) to produce my tracks. One mainstay of DnB was chopping up breakbeat samples to use sped up. Tools like Recycle came out to slice and chop drum break wav files into separate beats to re-sequence and add effects to.

Back then I had Recycle but not Reason or any sort of DAW that supported .rex files. I ended up just exporting the individual slices as separate .wav files and pulling them into FL Studio as sample tracks. I’d then just bang around on the step sequencer until I got something rolling along.

It seemed that most producers were taking the breaks and also exporting the corresponding MIDI timing and maybe quantizing that and possibly shuffling a few sections around. My approach was a bit different. I would group all of the like-sounding samples (kicks, snares, hats, etc) and put them in adjoining tracks. So out of 8-12 samples in a breakbeat I’d have 3 kicks, 4 snares, and some hats all lined up in adjacent tracks. Then it’s a matter of coming up with an interesting beat that doesn’t sound repetitive by experimenting with layering or just alternating which kick or snare is playing to keep things interesting. FL Studio made this pretty easy since each sample was on an individual track and you could do anything you wanted to an individual sample. 

The drawback of this approach is that now the project has a ton of single samples and there are many tens of tracks devoted to just drum breaks. It got kind of confusing to get to the point where you’re focusing on finishing a track at that point. 

So fast forward to today. I want to do some more breakbeat stuff and I really want to stay in Ableton and not use FL Studio for all the drums. Yes I could pull FL in as a VST plugin but I wanted to try out some slicer VSTs instead.

I remember one called Geist from back in the day. I dusted off my copy recently and found that the product is basically discontinued. It’s also like a full DAW in a plugin and supports so many different things it’s kind of overkill for what I want to do. I might look back at it in the future but for now it’s too much. I also noticed that it had a quantized grid sequencer and I never figured out how to get a piano roll or un-quantized sequencing out of it.

I checked out TAL-drum as well. This is another oldie but it’s got an updated version that looks pretty awesome. It’s very powerful but I had a hard time setting up layers easily. It’s simple to do things like split out the slices to pads and even change where in the parent sample the slice comes from on the fly. However it was difficult to do things like get a velocity spread set up across layers and get like sounds on different layers. The interface is modal so you can’t see the pads and the edit screens at the same time. It seems like I’m always flipping back and forth. It does have good modulation and routing but I’m not seeing how to get arbitrary MIDI CCs mapped into the mod matrix.

My favorite so far has been Speedrum. It’s not quite as featured as the others but has all the basics. The most salient feature for me is that it’s trivial to assign slices to layers in any pad right in the main interface. The UI is not modal so there is only one main screen. Once a sample is loaded in the slicer you can drag a slice to any pad and it’s added as a layer. I might be missing something but I wasn’t able to figure out how to easily add a slice to a layer in TAL drum. For now this is the killer feature for me. Getting a breakbeat wav file out of my library and into the slicer and from there to the pads in grouped drum layers is a great start. Everything else is gravy. Speedrum does have a compressor per pad and one global compressor that sounds pretty good and the obligatory delay and reverb sends. I’m more likely to use external effects, but it’s certainly simpler to do in the plugin especially to avoid using multiple outputs.

For completeness I will mention that I have also tried the FL Studio Slicex plugin which is included with Producer Edition of FL Studio. It’s nice but not a pad-style plugin. It’s got a 303-style sequencer thing and an interesting modulation system. The modulators are called “effectors” and consist of envelopes and settings that can be applied to several slices at once.

Another random slicer is LiveSlice, which I tried out long ago in an attempt to do live recording directly into a slicer so I could retrigger myself live. It does work since LiveSlice has very flexible MIDI control. A CC message can be used to enable loop recording on the fly so live audio can be sliced in near-realtime and triggered immediately. It supports scenes and sequence groups but is otherwise a little bit limited. I don’t see myself using LiveSlice for non-realtime production.

That was a long diatribe about slicers. Hopefully I look back at this and remember all the random crap I tried out and why I decided to use Speedrum in the end!
