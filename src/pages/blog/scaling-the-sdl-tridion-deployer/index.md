---
title: "Scaling the SDL Tridion Deployer"
date: 2012-12-28T05:54:05.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

coverImage: Drawing2.jpg
---

\[alert\]Originally Featured on Building Blocks [blog](http://blog.building-blocks.com/scaling-the-sdl-tridion-deployer "Building Blocks Blog")\[/alert\]

On a recent project we were met with a problem, the publishing pipeline could not handle the volume of publish transactions required. The publish queue would regularly grow to unacceptable lengths and important, even time critical, publish actions were delayed.

**Why?** Well there was no one culprit; all pieces of the puzzle were partly to blame:

1. We were publishing too many pages for the content model (inherited)
2. The templates were taking to much time and resource to render (inherited)
3. The Deployer was simply overwhelmed by the number of publish transactions it was having to process

Our first attempt to improve the situation was to investigate the Deployer; if the Deployer could handle the load, the other two culprits could be tackled over time. To begin with the Deployer was the limiting factor.

**So why was the Deployer a bottleneck?** The Tridion Deployer has some limitations, specifically when it comes to handling large volumes. My investigation lead me to the conclusion that, to a differing extent the Deployer is a bottleneck in a large volume publishing projects in both the 2009 and 2011 versions of Tridion. In Tridion 2009 the Deployer is truly single threaded, processing a single item at a time. In Tridion 2011 there has been some improvement; the Deployer is somewhat multi-threaded. However, in our situation, when we publish all pages in a single fashion, the performance improvement would be negligible.

**So what next;** how can we fix the problem? If a single Deployer can not handle the number of publish transactions, can two, or three, or more? First our existing infrastructure; we had a pretty standard setup. A Tridion cluster publishing via HTTP to a single Deployer, which then synchronized to the content folder of the website cluster as shown below.

[![Current Architecture](http://67.205.159.130/wp-content/uploads/2012/12/Drawing1.jpg)](http://www.mrgn.co/2012/12/scaling-the-sdl-tridion-deployer/drawing1/)

The existing Infrastructure was simply overwhelmed by the volume of publishing.

## Solution

We decide to investigate the plausibility of a multi-Deployer infrastructure, and after several iterations of tweaking we arrived at our current architecture, which at the moment is handling the publishing of several thousand pages a day.

[![New Tridion Arcitecture](http://67.205.159.130/wp-content/uploads/2012/12/Drawing2.jpg)](http://www.mrgn.co/2012/12/scaling-the-sdl-tridion-deployer/drawing2/)

 

Hopefully the diagram is pretty self explanatory (please ask questions) with the pipeline remaining largely unchanged with a few key additions. Firstly the Tridion publishers are now set to publish to a single load-balanced URL, which is then split across several Deployers. A key fact is that the load-balancer is configured for sticky sessions, meaning that the publisher (when requesting the status of a published item) will return to the same Deployer instance as to which it delivered. The Final addition; the now clustered Deployers all deploy to a single shared filesystem and this filesystem is replicated to the delivery cluster.

To reduce infrastructure costs we are hosting multiple Deployer instances on the same host server, using multiple instances of our application server.

> At the moment we are running this architecture with no problems, and achieving very high publishing throughput. However, there is at least one possible draw back, depending on your setup there is a chance of race conditions creating inconsistent content. Imagine the scenario, Page A is published as part of a large transaction (that will take at least several minutes to deploy) and is picked up by the first Deployer. While still in deployment an editor updates Page A, publishes on high priority and it is picked up by Deployer 2. Deployer 2 finishes first, and deploys the most recent version of the page, closely followed by Deployer 1, which reverts Page A back to one version ago. I feel the chances of this are quite slim (for us at least, as we publish single pages), and could be mitigated with training and process, as of yet, we have not knowingly been victim of this scenario. Also, we do not utilize the Broker database; additional testing would be required if factoring in dynamic content delivery.

**N.b.** This setup is all based on Linux Deployers and delivery servers using RSync and Apache Tomcat. There maybe additional concerns in a Windows environment. Please report back if you try this out.
