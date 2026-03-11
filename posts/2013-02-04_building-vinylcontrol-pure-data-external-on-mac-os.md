---
title: "Building vinylcontrol~ Pure Data external on Mac OS"
date: 2013-02-04T16:53:26-08:00
url: https://audiodestrukt.wordpress.com/2013/02/04/building-vinylcontrol-pure-data-external-on-mac-os/
id: 564
categories: Uncategorized
tags: 
---

# Building vinylcontrol~ Pure Data external on Mac OS

I just started a Pure Data project that interfaces with my turntables using Traktor Scratch timecode vinyls. In order to read the timecode data in Pure Data we need an external PD plugin object (called an external in PD parlance). There is an existing wrapper around libxwax called [vinylcontrol~](http://karhumusic.sesser.at/vinylcontrol/vinylcontrol.html) (PD objects that deal with audio-rate data are suffixed with a tilde by convention).

I’ve used this external on Linux before, where I had to compile it myself for a 64-bit architecture but on the Mac it was a little harder for me to get things working. To make a long story short, the most common PD distribution is built as a 32-bit binary application, and gcc tries to use the 64-bit toolchain by default on Mac.

Vinylcontrol is written using the [flext wrappers](http://puredata.info/Members/thomas/flext/) for PD which allows externals to be written using c++ and built on multiple platforms. The flext system is sort of like autoconf for PD. 

Installing flext on the Mac could be an article in itself, but I was able to get it to work by simply following the documentation so I’ll go into it here only briefly. By default, the flext build system compiled universal binaries of libflext-pd.dylib (both 64bit and 32bit) and installed them in /usr/local/lib. The default flext configuration files included with vinylcontrol were set so that libflext was found by the linker without any additional configuration.

Check out flext from svn:

```

$ svn co https://svn.grrrr.org/ext/trunk/flext flext

```
Build using:

```

$ ./build.sh pd gcc

```
The way flext works you’ll have to run this a few times, as there are some intermediate files generated that you might have to edit for your environment.

I did need to modify the config-mac-pd-gcc.txt file to point to the proper path where my PD installation was.

```

PDPATH=/Applications/Pd-0.43.4-extended-20130105.app/Contents/Resources

```
To install flext libraries and headers in the right places where vinylcontrol can find them, run:

```

$ ./build.sh pd gcc install

```
Untar the vinylcontrol sources and take a look at buildsys/config-mac-pd-gcc.txt. You might have to run build.sh once to generate this file. There are some antiquated flags here for G4 macs that need to be removed or commented out:

```

# optimizations for G4
# OFLAGS+=-mcpu=G4
# UFLAGS=-faltivec -ffast-math

```
-ffast-math is a valid compiler optimization but I left it out when I compiled. I might try putting it back in there later. -faltivec is for G4/G5 CPUs, and will generate a compiler error if specified for an Intel architecture.

I also had to specify a i386 (32bit) architecture in order for the linker to link the compiled external against the 32bit PD binary. The flext binaries were universal, so they linked ok but PD did not. The error messages get a little verbose so it can take a while to get to the root of things. Using the “file” command on generated binaries can help debug things by showing the architecture that the binary was compiled for.

I specified the architecture for the compiler using user flags:

```

UFLAGS+=-arch i386

```
I specified the architecture for the linker using LDFLAGS:

```

LDFLAGS+=-arch i386

```
Compile like this:

```

$ ./build.sh pd gcc

```
The build output shows up under pd-darwin/. I copied release-shared to ~/Library/Pd to install the external for my user account. I’m not sure what multi and single are. I believe that since I forced the architecture these will be all the same, but I’m not completely sure.
