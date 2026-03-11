---
title: "Hacking the McMillen SoftStep"
date: 2013-02-15T14:48:55-08:00
url: https://audiodestrukt.wordpress.com/2013/02/15/hacking-the-mcmillen-softstep/
id: 578
categories: Uncategorized
tags: 
---

# Hacking the McMillen SoftStep

![](https://i0.wp.com/www.keithmcmillen.com/products-images/p-product-softstep/over-hardware-softstep-top-view_R.jpg)

I recently got a [SoftStep](http://www.keithmcmillen.com/softstep/overview) foot controller from Keith McMillen Instruments and I finally got a chance to play around with the raw data from it in [Max/MSP](http://cycling74.com/products/max/).

I won’t go into too much detail here except to note some details about what data you get from this thing and how the sensors on the pads are oriented.

In order to get the raw sensor data you need to grab the [SDK from KMI](http://www.keithmcmillen.com/softstep/downloads/) for your platform. There will be a Max patch and two Max externals included in the SDK download. One of the externals handles IO to the device and the other takes the raw data stream and “cooks” it into higher level messages. Actually I think the raw data is accessible using ctlin, you only seem to need the externals to send LED and backlight data to the device.

The raw data stream consists of 4-byte records. Each byte represents a corner of the pad. There are sensors on each corner of the pads. the first byte is the upper left corner of the pad. The numbers continue clockwise around the pad.

I noticed when I first got the pedal that the centers of the pads aren’t very sensitive. This makes a lot of sense now that I’m digging into how this pedal works. When actuating the pads by foot, the center region is rarely actuated directly anyway. When actuating the pads using a finger on the center of a pad, nothing but the firmest press will be registered. However, pressing on one of the corners will result in an immediate response.

The demo patch has some interesting subpatchers that do things like key lockout and x-y navigation smoothing. The pedal firmware itself can do this as well, so possibly Max was used to prototype some of these features?

![softstep-maxmsp](images/2013-02-15_hacking-the-mcmillen-softstep_softstep-maxmsp.png)
