---
title: "Translation Mananger (TMS) Plugin to Translate the Components on Pages"
date: 2015-12-16T10:40:14.000Z
description: 
featuredpost: false
tags: 
  - plugin
  - SDL Tridion
  - SDL Web (SDL Tridion)
  - tms
  - Translation

---

When you start a translation in SDL Tridion on a Page, you are given the option to "translate components". However, this option will translate those components in the same location as the page, the current (context) Publication.

[![2015-12-16 02_53_28-Windows 10 on SF01-8CLVD12 - Virtual Machine Connection](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-16-02_53_28-Windows-10-on-SF01-8CLVD12-Virtual-Machine-Connection.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-16-02_53_28-Windows-10-on-SF01-8CLVD12-Virtual-Machine-Connection.png)

The solution to this is a Translation Manager Plugin, which I explain in more detail here: [http://blog.building-blocks.com/technical-tips/translation-manager-plugins](http://blog.building-blocks.com/technical-tips/translation-manager-plugins)

The plugin, attached to the "job saving" event trigger, will detect any pages within a translation job. If a page is detected, and is marked "translation components" it will then create a secondary translation job (in the correct context Publication or based on business rules) containing the pages components, appending the job title with "- components" for easy identification.

[![2015-12-16 03_12_16-Windows 10 on SF01-8CLVD12 - Virtual Machine Connection](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-16-03_12_16-Windows-10-on-SF01-8CLVD12-Virtual-Machine-Connection.png)](http://67.205.159.130/wp-content/uploads/2015/12/2015-12-16-03_12_16-Windows-10-on-SF01-8CLVD12-Virtual-Machine-Connection.png)

A simple example is shown below; more complex business rules could be added as required.

 

https://gist.github.com/chrismrgn/2e2b6290997dc2d1fdbc
