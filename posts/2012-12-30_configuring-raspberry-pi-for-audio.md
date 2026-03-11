---
title: "Configuring Raspberry PI for audio"
date: 2012-12-30T01:45:25-08:00
url: https://audiodestrukt.wordpress.com/2012/12/30/configuring-raspberry-pi-for-audio/
id: 525
categories: Uncategorized
tags: 
---

# Configuring Raspberry PI for audio

I now have my Raspberry PI device in hand and I’ve been trying to get it set up for some audio fun. Some things were pretty painless, like setting up Pure Data. I installed the Pd-extended Debian package and used apt-get to install missing dependencies and I was off to the races.
However, getting Jack to work was a different story. Actually, “was” is not the right word, as I’m still trying to get it working.
From what I have read so far, there are some known limitations with the onboard audio device on the PI, which is fine since I’m looking to use USB audio for the most part. However, it’s still not completely clear to me what limitations I’m up against. There seem to be some restrictions on shared memory. However I’m still not sure if pinning memmory/mmap is not supported at all by the driver or if I can fix this with limits.conf. I have played around with a lot of settings so far but I haven’t come up with anything definitive yet.
Things I’ve tried:
Running jackd as root
disabling realtime priority
disabling memory locking
using the dummy audio device
I’m getting an error once things go sour:
Bus Error
It seems that once jackd blows up on me, I keep getting this error. Running PD will give me this error when previously it would work before trying to run Jack.
I have seen reports that building Jack from source on the PI will work, but I don’t have a cross compiler set up yet for the PI and I’m not patient enough to build on the device. I built node.js the other day and it took 2h to compile on the board!
Here are some links that have gotten me closer so far:
http://www.raspberrypi.org/phpBB3/viewtopic.php?p=110801
http://www.raspberrypi.org/phpBB3/viewtopic.php?f=41&t=5787
