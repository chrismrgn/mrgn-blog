---
title: "SDL Web 8.5 in Docker - \"Server\" Service Error"
date: 2017-12-27T15:54:02.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

This is a very quick post, but hopefully it will save someone else the many wasted hours I've spent on this.

My aim was to try and dockerize an entire  SDL Web environment, therefore being able to have a quick POC/Dev/StackExchange question environment that I could spin up and dispose when I wanted.

So I started with the hardest part, the Content Manager.

I'd planned to install the Content Manager portion of SDL Web with an unattended install.However, after many hours of false dawns I've found what seems to be a roadblock, unless anyone else has a work-around?

While trying to lookup the user information, the installer makes a few calls as shown below and then bombs out of the install:

[![](http://www.mrgn.co/wp-content/uploads/2017/12/install-error.png)](http://www.mrgn.co/2017/12/27/sdl-web-8-5-in-docker/install-error/)

These calls rely upon the "Server" Windows service (otherwise known as the "LanmanServer") which is not currently supported in the Windows Server Core Docker image.
