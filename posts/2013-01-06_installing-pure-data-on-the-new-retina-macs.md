---
title: "Installing Pure Data on the new Retina Macs"
date: 2013-01-06T11:11:14-08:00
url: https://audiodestrukt.wordpress.com/2013/01/06/installing-pure-data-on-the-new-retina-macs/
id: 527
categories: Uncategorized
tags: 
---

# Installing Pure Data on the new Retina Macs

I’ve just gotten a new Retina MacBook Pro and while I’m not going to use it for audio most of the time, I wanted to get Pure Data running on it so I could use my Guitar Hero patches without high latencies ([hid] is available on the Mac version of Pure Data).

Anyway, there is a build of Pure Data that runs on Lion just fine, but I ran into the issue of needing an X server to display the patches. Running PD for the first time will show the main PD window but you’ll get a notification that you need an X server in order to run any patches.

From what I understand, until recently Mac OS shipped with X11.app, which was the default X server implementation on the Mac. Mountain Lion apparently doesn’t come with this anymore, and you have to get XQuartz. XQuartz installs just like a regular userspace application, but ends up under Applications/Utilities. Presumably this means that it can be uninstalled easily by deleting it from Applications. I bring this up because I want to be able to keep this machine relatively free of legacy stuff for development purposes, and it initially wasn’t clear to me if installing X11 would cause any other problems with Quartz or the Mac window manager (it didn’t so far).

Once XQuartz is installed you have to log out and back in again to get the DISPLAY environment variable to be available when PD is started up from the dock. It seems like there should be a way to just restart the dock maybe or finder and get this to work without logging out, but I don’t know it.

With XQuartz PD ran just fine. The only difference on Retina displays is that the windows are running in what they are calling pixel doubled mode. This means that the patches look a little blurry, like they have been blown up without any additional anti-aliasing because, well that’s what is happening. Kind of like running an iPhone app on an iPad I guess.
