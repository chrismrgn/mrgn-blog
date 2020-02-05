---
title: "SDL Tridion (SDL Web): Bundles"
date: 2015-12-17T07:49:31.000Z
description: 
featuredpost: false
tags: 
  - Bundles
  - SDL Tridion
  - SDL Web
  - SDL Web (SDL Tridion)

---

Bundles, until recently, had mostly escaped me. I’d had no reason to use them, and had not made the effort to investigate them.

Recently all that changed. I decided it was time to look into Bundles and how they could benefit my implementation.

Before getting started on a few things I’ve learn and how I’ve been using them, what are Bundles?

Bundles are a new type, introduced in SDL Tridion 2013. They are “similar” to folders, in that you can put items in them but behave a little differently

A few interesting facts I’ve learnt about Bundles, along the way:

- You can have a metadata schema
- You can localize them, but like a folder, the contents is not localized. Only the Bundle itself is localized, so you can change name or metadata
- You can manually start a workflow on a Bundle, at any time, not just at save
- You can publish a Bundle, but this should be treated like publishing a Structure Group. It is one transaction, and can if large take some time to process.
- You can Content Port a Bundle, which gives it some interesting usages
- You can translate a Bundle (and the items within it)
- You can’t add items to a Bundle except in the Publication it is created

[![2015_12_17_02_40_30_3D_Builder](http://67.205.159.130/wp-content/uploads/2015/12/2015_12_17_02_40_30_3D_Builder.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015_12_17_02_40_30_3D_Builder.png)

So how have I been using Bundles? I’ve used them in many of the ways above

- Scope – Bundles are a great way to group items to form a “scope” or “unit of work”. Press releases, images, videos, articles, product components all grouped together for easy tracking and deployment e.g. new product release

[![2015-12-17 02_42_39-Start](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-17-02_42_39-Start.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-17-02_42_39-Start.png)

- Translation – translating Bundles is a nice way to initiate the translation of a collection of items at the same time. In conjunction with my previous post, LINK, I send Bundles for translation and extract the component of each Page to also be translated
- Workflow – Bundles all editors to work on a “scope” for several days or weeks, and when it is ready start the Workflow for sign-off (just be careful people don’t publish while you are preparing, but before Workflow starts). I find Bundles and Bundle Metadata make an interesting for custom notification and assignment details, such as who to email when the Bundle Workflow completes
- Releases – Bundles are great as references for a release. Add all the changes items during a release or sprint to a Bundle, and then Content Port (or even better automate) between environments
- Deployment – If “scopes” are defined globally, and they have strong boundaries, scopes can be selectively published by local markets based on preference e.g. we do sell that product, publish the product scope (this could be particularly interesting when combined with the Import Export service, and a Continuous Integration (CI) process)

Overall I am growing to love Bundles, and will continue to add more information as I learn it.
