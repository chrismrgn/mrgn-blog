---
title: "Deployer Workers in Docker"
date: 2000-01-01T00:00:00.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

As part of my review of SDL Web 8.5, I wanted to try out the new approach to content deployment (Separation of Content Deployer role into endpoint and worker). I also saw this as an opportunity to play with Docker, as I've got a Windows Server 2016 machine up and running.

To really get an accurate picture, I wanted to try a truly scaled out system. Below are the steps and results:

1. Install Docker (if this is your first time setting up Docker, on Windows Server 2016, [this article might help](https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-server))
2. Create a Redis server (there is no official Redis server based on Windows, so I used [this one](https://hub.docker.com/r/alexellisio/redis-windows))
    1. docker run -d -p 6379:6379 --name redis alexellisio/redis-windows
    2. Use the https://redisdesktop.com/download to look at Redis data
        1. You need the IP address to connect to Redis, which you can find using
            1. docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" redis

 

docker exec -ti CONTAINER\_NAME powershell -> Enters PowerShell window to see what's going on

Get-Content FILE\_NAME -> To open log files

docker build -t chrismrgn/deployer-endpoint . -> Build the machine
