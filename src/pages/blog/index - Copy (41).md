---
title: "Publishing from SDL Web 8"
date: 2015-12-07T20:43:17.000Z
description: 
featuredpost: false
tags: 
  - SDL Web
  - SDL Web (SDL Tridion)

---

After reading Rob Stevenson-Leggett's post on Topology Manager I was intrigued, and thought I need to try setting up what used to be known as a "Publication Target".

As Rob describes, the settings in the administration have disappeared and migrated under the Publication node of the Content Management tab.

The first interesting thing I noticed, besides the name change to Business Process Type, is that they BluePrint! Adding a Target to a Publication adds it to the BluePrint. It can even be localized at lower levels... interesting... It gets a little less interesting, as it seems all you can do following localization is change the name. Maybe useful for translation in local markets, but not too exciting as a developer.

The first step to setting up a Business Process Type is to follow the documentation and install all the desired Content Delivery pieces, as described [here](http://docs.sdl.com/LiveContent/web/pub.xql?action=home&pub=SDL%20Web-v1&lang=en-US#docid=GUID-F226B4FA-2F03-494C-9DC6-8D66EDF472BA&addHistory=true&query=&scope=&tid=&filename=GUID-F226B4FA-2F03-494C-9DC6-8D66EDF472BA.xml&resource=&inner_id=&toc=false&eventType=lcContent.loadDocGUID-F226B4FA-2F03-494C-9DC6-8D66EDF472BA). Once they are configured, and registered with discovery service, you will see them in the CME as shown below (Rob's post does a great job of describing Topology Type and Purpose).

[![Topology](http://67.205.159.130/wp-content/uploads/2015/12/Topology.png)](http://67.205.159.130/wp-content/uploads/2015/12/Topology.png)

 

From this window, you get some options to give name, description, approval status (for Workflow), Priority default (nice new addition to allow Live to be prioritized) and security (who can publish by group or individual)

The last important tab is Bundle Schemas -- and I need to investigate this a little more. Once I have a better grasp of it, I'll add a blog post!
