---
title: "Cassette deck pitch control"
date: 2020-03-15T11:42:33-08:00
url: https://audiodestrukt.wordpress.com/2020/03/15/cassette-deck-pitch-control/
id: 871
categories: Uncategorized
tags: 
---

# Cassette deck pitch control

I got around to playing with the pitch control circuit on the cheap Amazon cassette recorders. The circuit uses a 500 ohm trimmer and an AN6650 IC speed controller.
Most pots I have are in the 10k-500k range so I didn’t have anything close to 500 ohms. I decided it was probably a voltage divider anyway so the actual value shouldn’t matter too much.
I wired up the 10k pot and observed that the range increased quite a bit from basically a dead stop all the way up to 160 rpm (measured at the take-up reel). I measured another unmodified unit and the max rpm was 90. I’m not sure why this was so maybe the circuit isn’t really a voltage divider.
Application notes for the 6650 seem to use a 1k pot rather than 500 ohms.

C58 is 20uF, C22 is 100uF and C6 is 220uF. I can’t read out the other SMD caps.
In any case it’s kinda cool to have such a huge range but I’m worried it will be hard to control. I’m using a linear pot, and it’s not clear whether the original 500 ohm trimmer was linear or log taper. I will try a log taper pot and see if that gets me better control since the first half of the linear taper is basically useless and runs the motor at full speed.
I might also look into some multi-turn potentiometers as well.
