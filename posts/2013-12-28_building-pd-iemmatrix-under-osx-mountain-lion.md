---
title: "Building PD iemmatrix under OSX Mountain Lion"
date: 2013-12-28T18:07:55-08:00
url: https://audiodestrukt.wordpress.com/2013/12/28/building-pd-iemmatrix-under-osx-mountain-lion/
id: 787
categories: Uncategorized
tags: 
---

# Building PD iemmatrix under OSX Mountain Lion

It’s often a trial by fire to build Pure Data externals despite cross-platform build systems like flext designed to make the job easier. I’ve blogged a little bit about getting some [arcane externals to build before](https://audiodestrukt.wordpress.com/2013/02/04/building-vinylcontrol-pure-data-external-on-mac-os/), so I’ll continue my quest to document my builds here.

Iemmatrix is a matrix math external for Pure Data. Those of you working with PD will realize that there are native arrays but nothing that deals with two-dimensional data. Iemmatrix fills that void with some efficient methods of manipulating matrix data.

As I noted before, 64bit versions of OSX will try to build 64bit libraries, so we have to take care of CFLAGS and LFLAGS appropriately. The one difference with iemmatrix is that it will try to build a shared library, and on my version of PD (0.43.4-extended OSX 32bit), this is not possible. The linker will link against the pd binary, which is not a shared library.

I set the following environment variables

```

$ export LDFLAGS="-arch i386"
$ export CFLAGS="-arch i386"

```
Before running configure, edit configure.ac and comment out the line that sets the -shared flag by prepending “dnl”:

```

dnl AC_CHECK_LDFLAGS([-shared])

```
After running configure like this:

```

$ ./configure --with-pd=/Applications/Pd-0.43.4-extended-20130105.app/Contents/Resources

```
I was able to make and get the iemmatrix.pd_darwin binary.
