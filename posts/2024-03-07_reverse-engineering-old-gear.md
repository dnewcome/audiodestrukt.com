---
title: "Reverse engineering old gear"
date: 2024-03-07T08:26:04-08:00
url: https://audiodestrukt.wordpress.com/2024/03/07/reverse-engineering-old-gear/
id: 1190
categories: Uncategorized
tags: 
---

# Reverse engineering old gear

I have a lot of random audio gear at this point. Drum machines and USB Midi things. Sometimes I get the crazy idea that it would be sweet to upgrade them with custom firmware. Sometimes I do a little hardware hacking on them to enable foot switches or something similar.

I looked into trying to figure out how the MC303 was designed. It turns out that the microcontroller architecture is pretty obscure and is only supported by some old compiler that I haven’t been able to find. Also there are a lot of custom ASICs for sound generation from Roland and it’s not possible to get data sheets for them. So it’s going to be a long slog of trying to map out the memory addresses and things using an in-circuit debugger or something.

I then thought maybe it would be easier to do a more modern device like the Akai Fire. This at least has a more modern ARM cpu. It has a serial debugging port header on the board already so it looks a little more promising. I was hoping to find a firmware update somewhere online but since this product was basically dead at release, there haven’t been any updates to look at so the first step I’d have to try to recover the existing firmware from the device and hope that there isn’t a lock bit set on the chip.

Other approaches might be to just replace the CPU with something else. I could theoretically just unsolder the chip and replace it with something that might be pin compatible or just put an adapter board on.

I ran across some articles where someone put some thought into reversing the MC-505. I have one of those so maybe I will start there since it has a more modern CPU that GCC supports.

I wonder what other bits of gear might be good candidates? Maybe I should start with the Synthstrom since the firmware is now open source already.
