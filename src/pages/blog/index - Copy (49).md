---
title: "Testing if a PublicationTarget is SiteEdit Enabled in the Razor Mediator"
date: 2015-06-03T21:54:47.000Z
description: 
featuredpost: false
tags: 
  - razor-mediator
  - SDL Tridion
  - SDL Web (SDL Tridion)

---

Often it is desirable to know in a template whether or not the Publication Target you are publishing to is XPM (Experience Manager) enabled.

The base TOM.Net API PublicationTarget class does not contain a property flagging this setting, it is stored in application data.

To get a Boolean of whether or not it is enabled for the Publication Target you can use Razor code as below

\[gist id="e18842da251747eea767"\]
