---
title: "SDL Web 8.1.1 - Optimizations"
date: 2016-11-02T20:12:46.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

The SDL Web 8.1.1 (or Cumulative Update 1 for SDL Web 8) release had some nifty features, which had escaped my radar.

Here's a quick summary of the ones I've found most useful, and a link to the full [release notes](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v1/GUID-35A551C9-FE77-47CD-A547-3EC8FEB4B9B6):

###### Micro-service Quick installers

Installing 3, 4, 5 or more micro-services can be a real pain. It is repetitive and prone to mistakes. SDL Web 8.1.1 comes with some helpful scripts to automate that installation. Look inside the \\INSTALL MEDIA\\Content Delivery\\resources\\quickinstall folder for a Powershell and Bash version of the quick install scripts

Powershell Example: Execute the following for a guide to using the script

.\\quickinstall.ps1 -help

###### Auto Registering Micro-services

Micro-services can now be configured to auto-register, saving you from re-regestering the scripts after update. Simple use the '--auto\-register' attribute as described below and in the [documentation](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v1/GUID-12D1D919-2D08-40C3-91A0-B6C0A643C29F).

> You can run the installation script for the feature (either installService.ps1, start.ps1 or start.sh) with the switch `--auto-register`. This automatically registers your microservice with the Discovery Service.

###### Parameters in the Storage Layer Configuration File

You can now use parameters in the storage configuration file, for items such as database names, servers or passwords (and anything else you want). These properties can be then set either in environment variables or as parameters when the service is initiated.

**Command Line Example (more in [documentation](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v1/GUID-39E1F200-1163-4A16-BCFF-F2E539B3498F))**

Storage Configuration Snippet

```markup
<Storage Type="persistence" Id="defaultdb" dialect="${dbdialect}"
  Class="com.tridion.storage.persistence.JPADAOFactory" generateDDL="true">
```

Command Line Argument

start.ps1 -Ddbdialect=ORACLESQL
