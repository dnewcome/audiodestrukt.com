---
title: "Running Pure Data patches full screen"
date: 2012-12-02T19:34:57-08:00
url: https://audiodestrukt.wordpress.com/2012/12/02/running-pure-data-patches-full-screen/
id: 500
categories: Uncategorized
tags: 
---

# Running Pure Data patches full screen

I’ve been working on some Pure Data patches that I intend to use as dashboards during live performance. I want these to be running on my personal monitor display that faces me. The audience won’t be able to see it but I still want to run full screen without any distracting borders, etc.

There is a Pure Data plugin called [KIOSK-plugin](http://puredata.info/downloads/kiosk-plugin) that is supposed to enable things like removing title bars and disabling context menus. I wasn’t sure if it would work on Windows initially, but I ended up getting it to work by paying attention to a small detail.

Installing the plugin is just a matter of extracting the archive to pd-extended\extra\kiosk-plugin. It’s not that obvious from the docs where it should go on Windows. If pd-extended is your Pure Data installation path, it will go under the “extra” directory under that. On Linux there is a directory called “pd-externals” that doesn’t seem to be consistent with Windows installations. As an aside, I’m using the “portable” version of PD that is distributed [without an installer](http://autobuild.puredata.info/auto-build/latest/Pd-0.43.4-extended-windowsxp-i386.zip). Note that the version is 0.43.4 as of this Writing. I’ve experienced performance issues with earlier beta versions.

Once the plugin is installed, it will be loaded the next time that PD is run. Configuration is done using kiosk.cfg, which is located in the plugin directory. This file is a little inconvenient at times, as many times you’ll want to override kiosk mode unless you are actually doing a performance.

The crucial thing to note is that auto-fullscreen doesn’t seem to work in Windows. Thus, the following setting will enable fullscreen-on focus (clicking the patch window):

```

KioskNewWindow True

```

When opening a patch for performance, simply click on the window that you want to run full screen and it should expand and hide its toolbar and OS chrome.
