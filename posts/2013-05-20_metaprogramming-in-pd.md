---
title: "Metaprogramming in PD"
date: 2013-05-20T22:57:52-08:00
url: https://audiodestrukt.wordpress.com/2013/05/20/metaprogramming-in-pd/
id: 701
categories: Uncategorized
tags: 
---

# Metaprogramming in PD

Metaprogramming is essentially writing code with code. It is a powerful tool used mostly in languages that have macros. But any time we have the ability to alter code at runtime meaprogramming is possible.

In PD we have ways of sending object creation messages to a subpatch. These messages are mostly undocumented features of PD, so we are kind of in the fringes here, but then, PD is mostly fringes for better or worse!

The message that is most useful to us in this situation is the “obj” message. Check [this page](http://puredata.info/docs/tutorials/TipsAndTricks) out for a big list of internal PD messages

In my case, there are many times where I want to create a big grid of some objects (say a Monome patch or something). This is easily done using a typical modulus and integer division solution for creating a coordinate matrix from a number series, then using these coordinates in a object creation message that targets our output subpatch. 

![pd-metaprogramming](images/2013-05-20_metaprogramming-in-pd_pd-metaprogramming.png)

The above code generates the following output:

![grid-pd](images/2013-05-20_metaprogramming-in-pd_grid-pd.png)

This can be used as-is or copied somewhere else. It might be nice to create some metaprogramming tools outside of the current project just to use for things like this. I’m still exploring whether this can be used to target the current patch (rather than a subpatch) and whether primitive objects like bangs or toggles can be created this way. If anyone figures either of those things, let me know!
