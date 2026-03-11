---
title: "Developing DSSI plugins"
date: 2012-05-23T20:44:32-08:00
url: https://audiodestrukt.wordpress.com/2012/05/23/developing-dssi-plugins/
id: 356
categories: Uncategorized
tags: 
---

# Developing DSSI plugins

I was looking around for a sampler instrument on Linux to test my Pedal Fighter project with, and while I remembered Specimen from a while ago, I remembered that there weren’t many samplers out there apart from the Linux Sampler project (which I’ve had problems with in the past – way too complicated for quick setups).
I dip my toes into the Linux audio development world every now and then, so I figured I’d take a look at the current state-of-the-art for Linux instrument plugins, DSSI (dizzy).
DSSI is basically VSTi for Linux, or LADSPA for instruments depending on your viewpoint. It is a spec that we can conform with to enable our code to be hosted in different programs such as Ardour.
I grabbed the DSSI development kit and compiled it. I had to grab the LADSPA SDK using APT (I’m using Ubuntu)

$ sudo apt-get install ladspa-sdk

After this I could build the sources using configure/make.
However in order to get the reference Jack host to work we’ll need the libjack development package which includes the headers.

$ sudo apt-get install libjack-dev

There are some other dependencies that I already had installed, but are worth mentioning. Liblo is the Lightweight OSC library.
I started looking through the code and the host looked to complicated to start with (the reference jack-dssi-host is 2000 lines or so) so I started with trivial_synth.c under examples/.
I looked around for an entry point. I noticed the following:

#ifdef __GNUC__
__attribute__((constructor)) void init()
#else
void _init()
#endif

_init(), is part of dlopen, which is used to load dynamic libraries at runtime. The init function constructs the plugin descriptors according to the LADSPA and DSSI specs. 
The following function is specified in the LADSPA spec, and returns the descriptor when called.

const LADSPA_Descriptor *ladspa_descriptor(unsigned long index)
{
    switch (index) {
    case 0:
    return tsLDescriptor;
    default:
    return NULL;
    }
}

The descriptor is where we specify the functions we want to use as callbacks for things like processing the chunk of audio or defining input and output ports.
The only thing further to understand is that the GUIs are separate standalone programs that communicate with the running plugin using OSC. You can start the GUI separately from the plugin and kill the GUI without affecting the execution of the plugin.
I had some problems getting the GUIs for the sample projects to show up when running the reference Jack host though. In order to get things working I had to actually install everything on my system using

$ sudo make install

The commandline options for running a GUI are kind of cryptic so here is what the GUI command looks like when it runs automatically from the Jack reference host:

$ /usr/local/lib/dssi/trivial_sampler/trivial_sampler_qt osc.udp://X200:12034/dssi/trivial_sampler/stereo_sampler/chan00 trivial_sampler.so stereo_sampler channel 0

It looks like the GUIs are installed alongside the plugins using a folder structure that follows the naming convention of the shared object file.
I’ll write some more once I’ve done some actual coding on a new plugin.
