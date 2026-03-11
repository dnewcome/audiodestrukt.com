---
title: "Tube amp design"
date: 2012-01-25T02:39:45-08:00
url: https://audiodestrukt.wordpress.com/2012/01/25/tube-amp-design/
id: 176
categories: Uncategorized
tags: 
---

# Tube amp design

I’ve been playing around with some different vacuum tube amplifier circuits on the bench recently. However, it’s hard to play around with anything but a starved-plate design given that I don’t have a high voltage power supply on the bench. It’s also hard to provide a proper load for the output tubes since that typically requires a impedance matching transformer, which I don’t have lying around.

I’ve used LTSpice for some of my previous circuit designs, so I set out looking for some vacuum tube models for it. In my search I found the Duncan Amps page, which had a nice simple [single-ended EL84 design](http://www.duncanamps.com/zips/6bq5_5w_amp.zip) already done in LTSpice.

Here I’m going to say a few things about the simulation and the circuit.

In order to run the simulation just hit Simulate->run. However, we need to know which test points are interesting. The speaker load is simulated with R2 on the schematic. So this is the output of the circuit that we’re interested in. Along the way we have three gain stages that we’re interested in looking at – namely the output voltages after each tube stage. These aren’t labeled as test points in the schematic, but they are going to be the grid voltages at the beginning of each stage.

In the next post I’m going to break this circuit down from beginning to end. In the meantime here is the original schematic. I’m going to annotate it with some test points next time.

![](images/2012-01-25_tube-amp-design_dunc-tube-amp-schem.png)
