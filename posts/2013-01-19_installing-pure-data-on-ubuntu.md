---
title: "Installing Pure Data on Ubuntu"
date: 2013-01-19T12:49:44-08:00
url: https://audiodestrukt.wordpress.com/2013/01/19/installing-pure-data-on-ubuntu/
id: 533
categories: Uncategorized
tags: 
---

# Installing Pure Data on Ubuntu

Getting PD working on Linux should be the easiest thing in the world, but I’ve found that it can be a little tedious to get just the setup that you want installed. 
Most of the time we want to have PD-Extended so that all of the PD externals that don’t ship with PD Vanilla are included. However, many times the PD-Extended distribution is lagging behind PD-Vanilla for a while.
PD can be installed from the APT repositories but again the version lags quite a bit sometimes.
Installing from source is one option, but in my experience it doesn’t always build cleanly for me and installation is a pain. There are some manual steps to getting the Tcl/TK UI pointed in the right direction and there are some path issues. Sorry if this seems kind of vague, but I don’t have a lot of notes from my previous attempts at getting a sane PD environment set up.
Short story is that if you are looking for a particular version of PD or some particular set of externals there might be some work to do when trying to get things running.
Fortunately there is a PD 0.43 64 bit .deb package out on puredata.info, so for now this solves my issue.
To install just download the .deb package and install using dpkg. To update unmet dependencies run apt-get.

$ dpkg -i Pd-0.43.4-extended-ubuntu-precise-amd64.deb
$ apt-get -f install

The next time I have to build from source I’ll post something here about it since it seems like I forget just how I did it the last time around.
