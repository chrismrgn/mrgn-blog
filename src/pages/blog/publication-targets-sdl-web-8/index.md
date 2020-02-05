---
title: "Publication Targets & SDL Web 8"
date: 2016-02-18T01:03:16.000Z
description: 
featuredpost: false
tags: 
  - SDL Web
  - SDL Web (SDL Tridion)

---

With the introduction of SDL Web 8, publishing has changed. Overall, once you get your head around it, Topologies (the new way of publishing) are a nice approach. They provide a clear separation between the Content Management and Content Delivery environments.

However, Topologies take some learning, and are slower to setup for quick demo situations.

If you want to use the old way, with Publication Targets, you can follow these instructions and the Publication Node will reappear

1. On the Content Management server browse to %TRIDION\_HOME%\\web\\WebUI\\Editors\\CME\\Configuration\\
2. Open the CME.config file
3. Find **enablepublishingmanagement** and change the value to **true**
4. Restart the Content Manager website
5. Within the Content Manager the Publishing node will be back
