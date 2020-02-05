---
title: "SDL Web: Staged Upgrades & Content Delivery as a Service"
date: 2015-12-21T13:13:40.000Z
description: 
featuredpost: false
tags: 
  - CDaaS
  - SDL Web
  - SDL Web (SDL Tridion)

---

I've written before about [staged upgrades](http://blog.building-blocks.com/technical-tips/upgrading-to-sdl-tridion-2013-the-staged-upgrade), and the procedural advantages that may bring depending on your organization. Being able to plan manageable chucks of upgrade activity certainly can be attractive, when dealing with a large eco-system.

In SDL Web 8, staged upgrades are certainly still an option, with the progress described [here](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v1/GUID-9681E815-15D0-4EC9-93C9-9E66CC3006D3) -- but there is something else interesting...

Looking at step 4. as shown below, what we have is the new Content Delivery stack, running against the existing (current) Content Management stack, but why is this interesting?

[![GUID-C0FE157A-294C-473A-86EC-C1D1F8AD38FE-low](http://67.205.159.130/wp-content/uploads/2015/12/GUID-C0FE157A-294C-473A-86EC-C1D1F8AD38FE-low.png)](http://www.mrgn.co/2015/12/sdl-web-staged-upgrades-content-delivery-as-a-service/guid-c0fe157a-294c-473a-86ec-c1d1f8ad38fe-low/)

In this setup, you can start to take advantage of some of the features of the [new content delivery stack](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v1/GUID-D1C8C3C7-445C-43DB-A1D1-2F1060E1F4F6), while your back-office is still being transitioned. It is common that back-office can take longer to migrate, due to tighter coupling to prerequisites etc.. and the need to find a suitable window for a Content Manager outage. A staged approach allows the Content Delivery team to keep progressing, while Content Management catch up.

The biggest Content Delivery improvement (and most exciting to developers) is the addition of the Content Delivery micro services or Content Delivery as a Service (CDaaS).

The new CDaaS exposes the dynamic content in your system via a RESTful web service, which can be consumed directly or via API libraries. Moving to CDaaS has many benefits, including:

- Separation of concerns between your website, web app, mobile app and the underlying SDL Web infrastructure - the two can be on distinct machines if desired
- Backwards compatibility - further optimizing staged upgrades in the future
- Reduce prerequisites - **No more JuggerNet, or Java required in your web application!**
- Scaling - web applications and CDaaS can be scaled independently
- SaaS - expose content to third-parties as a service, to cross sell/promote your content
