---
title: "Razor Mediator: Potential Memory Leak"
date: 2016-01-11T11:08:11.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

The Razor Mediator is a great community tool, which makes SDL Tridion (SDL Web) templating easy!

The out of the box settings work well, however there is something to be aware of if you are making changes. Changing some values can cause memory leaks and excessive memory usage within the Publisher Windows service!

#### The default settings

<importSettings includeConfigWhereUsed="**true**" includeImportWhereUsed="**true**" replaceRelativePaths="false" />

#### Warning

Changing either "includeConfigWhereUsed" or "includeImportWhereUsed" to false will cause drastically increased usage, especially during high publishing load.

#### Why would you change these?

The most likely reason is frequent development changes in the development environment. The mediator code detects changes to templates, and refreshes the cache, however it does not reflect changes to templates dependencies (i.e. imports).

Changing these settings mean that every time a template is executed it is reloaded (compiled), hence getting the latest dependencies.

#### Why the increase in memory?

Because templates are in memory as dynamic types, when they are removed from the cached template collection the memory is not released. As the template is compiled for every execution (and added to the template cache) the memory grows with every publish action.
