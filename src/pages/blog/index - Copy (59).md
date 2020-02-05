---
title: "Tridion Error - Stored Procedure Deadlock"
date: 2012-10-31T03:14:47.000Z
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

> A database error occurred while executing Stored Procedure "EDA\_PUB\_TRAN\_UPDATE \_PUBLISH\_TRANSACTION". Transaction (Process ID 87) was deadlocked on lock resources with another process and has been chosen as the deadlock victim. Rerun the transaction.

Cause:

> The number of deployer/publisher processes specified in the Tridion _Snap-in_ exceeds the number of CPU cores.

Solution:

> Update Publisher Settings, deployer and rendering threads to be less than or equal to the number of processors available.
