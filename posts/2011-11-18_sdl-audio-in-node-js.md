---
title: "SDL audio in Node.js"
date: 2011-11-18T02:03:40-08:00
url: https://audiodestrukt.wordpress.com/2011/11/18/sdl-audio-in-node-js/
id: 95
categories: Uncategorized
tags: 
---

# SDL audio in Node.js

I was looking around for a way to play sound from Node.js and found out that there is now a [SDL_mixer](http://www.libsdl.org/projects/SDL_mixer/) [module for Node.js](https://github.com/japj/node-sdlmixer). Previously I had looked at [Irrklang](http://www.ambiera.com/irrklang/) and the corresponding [Node module](https://github.com/tmpvar/node-irrklang) but I never felt that crazy about Irrklang.

A while back I was following the development of JSONLoops, which is how I found out about Irrklang. At one point that project was calling out to the shell to use aplay for playing back wav files. Marak went kind of crazy on Google Groups and put out a [bounty](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&ved=0CCgQFjAC&url=http%3A%2F%2Fgroups.google.com%2Fgroup%2Fnodejs%2Fbrowse_thread%2Fthread%2F5b62789562697956&ei=tivGTvb9DqHQiALPsanRDw&usg=AFQjCNHy-31vUjc4v37oRJ2iDDsKyAAXww) for someone to get some reasonable native audio library sorted out under Node.

So now as a result it looks like there is a nice SDL_mixer library for Node. I checked it out and it looks like just what the doctor ordered for what I’m thinking. Later on I’m still planning on getting [libpd for Node](https://audiodestrukt.wordpress.com/2011/10/24/project-libpd-module-for-node-js/) finished, but for a new project I have in mind this is perfect.

I have tested this library on OS X and also under Linux and it seems to work perfectly in both environments.

On Ubuntu Linux:

```

# apt-get install libsdl-mixer1.2-dev
# npm install sdlmixer

```
On OS X using Homebrew:

```

# brew install sdl_mixer
# brew install node
# curl http://npmjs.org/install.sh | sh
# npm install sdlmixer

```
Now go into the tests and run test.js to see if you get some sound!
