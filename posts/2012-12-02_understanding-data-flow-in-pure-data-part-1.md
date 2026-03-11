---
title: "Understanding data flow in Pure Data part 1"
date: 2012-12-02T18:01:58-08:00
url: https://audiodestrukt.wordpress.com/2012/12/02/understanding-data-flow-in-pure-data-part-1/
id: 487
categories: Uncategorized
tags: 
---

# Understanding data flow in Pure Data part 1

Quick, what is the difference between the following two patches?

Visually they are identical, but if you take a look at the number box at the output, that should give you a clue. The patch on the right has an off-by one bug in it that isn’t obvious by inspection of the patch. 
Execution in Pure Data happens depth-first right-to-left. However, this applies to the outlets of an object, not to multiple signals emitted from a single outlet. In the event that there is more than one connection made to the outlet of an object, they are processed in the order that the connections are made. Thus, the difference between the two patches above is that in the second patch the bang object was connected to the input before the right hand inlet of the subtraction operator was connected. This causes the subtraction operation to be evaluated before the updated value is sent to the input of the operator. That is, the previous stale value is used in the computation, causing the output to lag behind.
Bugs like this can be very hard to detect as sometimes the patch will be much more complicated than the simple examples that I have given above, and if the subtraction is evaluated by sending the bang message from some other part of the patch, it’s possible for the output to be correct some of the time and lagging at other times, making for a very tricky intermittent bug.
I consider this to be somewhat of a shortcoming in the Pure Data language, requiring us to be very strict when considering the order in which events occur. I’d like to treat PD in a more functional way, which may be the subject of some upcoming posts on Audio Destrukt.
The correct way to write the patch is the following:

Note that we introduced the “t” or trigger object. This forces strict ordering of messages following the Pure Data right-to-left rule. Thus, the input float, denoted by the “f” creation argument is output first, followed by a bang or “b” message to force evaluation. This construct has the added advantage of doing a little type conversion for us, so the bang object following the trigger is no longer needed and the patch can thus be simplified to:

I used this example because it brings up another common Pure Data design idiom, which is the inversion of a control value by subtracting the value from the max value. The subtraction object isn’t very intuitive to use this way, as it is designed to take a construction argument that facilitates decrementing the input value by some value rather than subtracting it from another value. There are several solutions to this problem, one of which being the previous example, which introduces the secondary problem of signal ordering that I just described.
A little-known fact of Pure Data objects is that their inlets may be assigned values based on a list sent to the first inlet of the object. Thus, we can assign both inlets of the subtraction operator simultaneously with a list before evaluation. This lets us simplify our patch as the following:

This construct requires an understanding of parameterized messages. The message box contains an argument for the inlet number and when changed, the message is composed and sent as a list to the subtraction operator, which is immediately evaluated and the output appears at the inlet of the final number box.
However, my favorite solution to this problem is to use the expr object to describe the entire operation succinctly and allow us to evaluate it directly without any external message composition. Here is an example:

The inlet parameter is described in the expression as $f1.
That’s all for this installment. I’m probably going to dig into another issue I ran across recently when computing multiple logical “and” operations next.
