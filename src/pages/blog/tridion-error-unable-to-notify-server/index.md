---
title: "Tridion Error - Unable to notify Server"
date: 2012-10-31T03:25:45.000Z
description: 
featuredpost: false
tags: 
  - Error
  - Error Series
  - SDL Tridion
  - SDL Web (SDL Tridion)

---

\[alert\]I use the Error Series to track the solution to common issues that are easy to forget. They are as much for my memory as public consumption.\[/alert\]

Error:

> Unable to notify "SERVER\_NAME". Reason: The requested name is valid, but no data of the requested type was found

Cause:

>  Unreachable servers in the database table, likely during a database upgrade or migration.

Solution:

> Update table **_dbo.QUEUE\_CONSUMERS_** in the Content Manager database setting all inactive/unreachable servers **_IS\_ONLINE_** value to Zero.
