---
title: "MIDI over Websockets with Socket.IO"
date: 2011-12-04T18:01:38-08:00
url: https://audiodestrukt.wordpress.com/2011/12/04/midi-over-websockets-with-socket-io/
id: 105
categories: Uncategorized
tags: 
---

# MIDI over Websockets with Socket.IO

In my last post I outlined how I used curl to send MIDI data over HTTP to a web app. The problem with this design is that HTTP has a lot of connection overhead that contributes to latency problems.
To address the latency issues, I set up the Node Web application to use Websockets for playing notes. The code on the server side is very simple:

var io = require('socket.io').listen(8030);

io.sockets.on('connection', function (socket) {
  socket.on('play', function (data) {
    play_drum( data.note );
  });
});

Here we set up a message called “play” that takes an object describing the note that we want to play.
The code above is pretty much boilerplate code. The trickiest part is the client. Ordinarily the Socket.IO client would be a Web browser. In order for us to pipe MIDI data to a Websocket request we’ll need a Socket.IO client. The Socket.IO guys now have an official client called Socket.IO-client.
Since we can handle stdin ourselves in Node, we don’t need xargs, and we can pipe the output of amidi directly to our node client program.

amidi -d -p hw:1,0,0 | node socketio-client.js 

See my previous post for more details on amidi and finding the correct device number for your MIDI controller.

var io = require( 'socket.io-client' );
process.stdin.resume();
process.stdin.setEncoding('utf8');

process.stdin.on('data', function (chunk) {

        // process arguments
	chunk = chunk.replace( '\n', '' );
	var args = chunk.split( ' ' );
	var jsargs = { note: args[1], vel: args[2] };
        
        // raise the play event
	socket.emit('play', jsargs );
});

Node.js requires us to unpause stdin. Once we do that we can listen for stdin.on() for data and raise the Socket.IO event when we receive data.
The latency is much better with this method, but still not great. I’m going to try implementing this using a browser-based client as well to see if it is any better.
The code for all of this is part of dub-siren.
