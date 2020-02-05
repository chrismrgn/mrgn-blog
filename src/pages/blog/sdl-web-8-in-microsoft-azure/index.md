---
title: "SDL Web 8 in Microsoft Azure"
date: 2015-12-02T21:29:57.000Z
description: 
featuredpost: false
tags: 
  - SDL Tridion
  - SDL Web
  - SDL Web (SDL Tridion)

---

SDL Web 8 has many exciting additions, as I've outlined in a post on the Building Blocks blog [here](http://blog.building-blocks.com/what-is-sdl-web-8).

One of the most exciting things, for me, was the added support for cloud databases SQL Azure and Amazon RDS (for SQL Server).

So as soon as I got my hands on the installer, I got straight to it, and here is the outcome:

Steps to setup (in MS Azure)

1. Create a database server, as below [![2015-12-02 15_37_14-Photos](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-15_37_14-Photos.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-15_37_14-Photos.png)
2. Create a Virtual Machine (I chose Windows Server 2012 R2)
3. Create the MTSUser, as per the documentation
4. Run the database scripts against the Azure database server URL from Step 1, as [per the documentation](http://docs.sdl.com/LiveContent/web/pub.xql?action=home&pub=SDL%20Web-v1&lang=en-US#docid=GUID-A1A8D2A1-7B2E-4FD0-8A81-908CAC1D133F&addHistory=true&query=&scope=&tid=&filename=GUID-A1A8D2A1-7B2E-4FD0-8A81-908CAC1D133F.xml&resource=&inner_id=&toc=false&eventType=lcContent.loadDocGUID-A1A8D2A1-7B2E-4FD0-8A81-908CAC1D133F)[![2015-12-02 16_21_13-Photos](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-16_21_13-Photos.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-16_21_13-Photos.png)
5. Continue to follow through the install, as documented, using the Azure database server URL where appropriate
6. Hey presto, SDL Web running against Azure SQL[![2015-12-02 16_28_16-Photos](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-16_28_16-Photos.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-02-16_28_16-Photos.png)

Next, I'll setup content delivery.
