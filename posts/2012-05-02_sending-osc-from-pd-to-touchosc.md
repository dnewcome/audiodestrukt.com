---
title: "Sending OSC from PD to TouchOSC"
date: 2012-05-02T11:47:54-08:00
url: https://audiodestrukt.wordpress.com/2012/05/02/sending-osc-from-pd-to-touchosc/
id: 264
categories: Uncategorized
tags: Live PA, TouchOSC
---

# Sending OSC from PD to TouchOSC

I’m playing around with some TouchOSC control methods currently. I’m running the fantastic Monome TouchOSC emulation and hoping to control my old PD sequencer with it.

I had a few issues getting the Hexler basic.pd demo patch to work, and it was a very simple thing in the end. You can grab their pd patch from the [documentation page](http://hexler.net/docs/touchosc-getting-started-osc).

I initially had the wrong IP address set up, and for some reason when you send the connect message without first disconnecting, PD won’t reconnect to a new IP address. I added a disconnect message to the patch like this:

![](images/2012-05-02_sending-osc-from-pd-to-touchosc_touchosc-pd.png)

I figured this out by adding a number box to the SendOSC output, which tells you if you are connected or not. Sometimes it pays to read the help patches in PD!
