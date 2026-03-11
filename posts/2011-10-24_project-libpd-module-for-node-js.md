---
title: "Project: Libpd module for Node.js"
date: 2011-10-24T13:52:38-08:00
url: https://audiodestrukt.wordpress.com/2011/10/24/project-libpd-module-for-node-js/
id: 20
categories: Uncategorized
tags: 
---

# Project: Libpd module for Node.js

A few months ago I started a project to build a native [Node.js](http://nodejs.org/) module around [libpd](http://gitorious.org/pdlib/pages/Libpd). The idea is to enable a way to run [Pure Data](http://puredata.info/) on the server to enable creation of multi-user audio applications on the Web using Node.js.

For those of you that are unfamiliar with Node.js, it is a server-side Javascript environment that is based around a non-blocking event loop. Node allows easy implementation of things like server push notifications (with [socket.io](http://socket.io/)) and is a perfect environment for message-passing web apps. I think that this could be huge for collaborative music on the Web since performance data is essentially event driven and message-based.

The current code is just a skeleton Node.js module that can load a predefined Pure Data patch and run it. There is still lots to do, and audio processing isn’t implemented at all yet.

If you’re interested in hacking on this, the code is [here on my github account](https://github.com/dnewcome/node-libpd). Fork away!
