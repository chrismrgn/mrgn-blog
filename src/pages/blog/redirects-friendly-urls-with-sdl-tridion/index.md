---
title: "Redirects & Friendly URLs with SDL Tridion"
date: 2015-05-25T23:44:01.000Z
description: 
featuredpost: false
tags: 
  - SDL Tridion
  - SDL Web (SDL Tridion)
  - url-redirects

---

Redirects and friendly URL's have been required in almost every project I have ever worked on. Whether it is to handle legacy URL structures or new marketing initiatives URL manipulation is a must.

Here is a quick guide to show how simple it can be to implement in SDL Tridion using the [IIS URL Rewrite](http://www.iis.net/downloads/microsoft/url-rewrite) extension.

1. Install the IIS URL Rewrite extension on your content delivery server(s) (plan this install through environments to avoid delay's later)
2. Create a simple new Schema "URL Rewrites" to allow editors to create rewrite rules with a required text field for _from address_ and _to address_ (Optionally add a description field to make it easier to maintain the URL's going forward)
3. Update your Web.Config to include a rewrite section as below (I prefer including the rules outside of Web.Config to avoid unexpected Application Pool recycles) \[gist id=490b3089dbc7a374632c\]
4. Create Component Template (using [Razor Mediator](https://code.google.com/p/razor-mediator-4-tridion/), including forced redirect to HTTPS) \[gist id=53338cd5b48c9803159a\]
5. Create Page Template (using Razor Mediator)
6. Create test Component and Page (preview Page to check templates are working and outputting in the correct format)
7. Publish Page
8. Restart the Application Pool
9. Test
