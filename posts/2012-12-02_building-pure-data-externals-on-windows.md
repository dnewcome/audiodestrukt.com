---
title: "Building Pure Data externals on Windows"
date: 2012-12-02T16:24:02-08:00
url: https://audiodestrukt.wordpress.com/2012/12/02/building-pure-data-externals-on-windows/
id: 473
categories: Uncategorized
tags: 
---

# Building Pure Data externals on Windows

I recently built the [beatpipe](http://puredata.info/downloads/beatpipe) external under Windows, and it had a few tricky things to remember so I’m outlining the process here.

Externals are usually pretty easy to build under Linux where the GCC tool chain is already installed, but on Windows you have several different ways that something can be built. Some externals need to be built with MS Visual C++. I’ll talk about that in another post. In the case of beatpipe, the author didn’t use the flext library and it looks like the Makefile was designed for gnu make and the Gnu C compiler, so I decided to try building with MinGW.

MinGW is the minimalist gnu for Windows environment, which is designed to provide enough compiler tools under Windows to hopefully build something that targets the Gnu compiler system. I was hoping that MingGW would be enough of an environment to build beatpipe. I think Cygwin could have been used otherwise, but Cygwin is pretty big and I’m not a huge fan of it for mostly that reason.

Installing MinGW still took kind of a long time since it pulls a lot of individual components down over the Web. I used the [bootstrap installer](http://sourceforge.net/projects/mingw/files/latest/download?source=files) for Windows to get it installed. I installed just the base system, but I selected the option for 

I grabbed the beatport source code and extracted it. I ran the mingw shell shortcut that gets installed by the MingGW installer and switched to the directory that I unzipped the sources to. Note that the Windows drive letters are mapped as /C, /D, etc. The ls command doesn’t show these so it can be confusing to figure out where you are on the filesystem. As an aside, the mount command does show these drive letters as mounted filesystems.

I put pd.dll in System32 temporarily so ld could find it. MingGW has a complex way of searching locations for libraries, which is [explained here](http://www.mingw.org/wiki/HOWTO_Specify_the_Location_of_External_Libraries_for_use_with_MinGW). I put m_pd.h in the source directory since the make file referenced pd somewhere else, and it was easier to just copy the header than to edit the make file. 

I ran make and ended up with beatpipe.dll. I installed it by copying the entire directory including the help patches to pd-extended\extra\beatpipe-1.0.

After all that, it actually worked, which is a small miracle sometimes when trying to build externals on Windows.
