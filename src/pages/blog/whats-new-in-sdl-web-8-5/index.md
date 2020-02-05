---
title: "What's new in SDL Web 8.5 (formerly SDL Tridion)"
date: 2016-12-21T22:00:54.000Z
description: 
featuredpost: false
tags: 
  - SDL Web
  - SDL Web (SDL Tridion)

---

SDL Web 8.5 (formerly SDL Tridion) has been released, and here are a few of the headline features you can expect. For full details, consult the documentation portal [here](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v5).

###### Content Manager

- **Data Storage & Migration** - Multimedia assets can now be stored outside of the Content Manager database, on the file-system or cloud blob storage such as Amazon S3 and Azure Blob. This is a big improvement, as with the ever growing popularity of multimedia rich websites that database could become a little unruly. This will drastically reduce the database size in many implementations, and help with performance and general maintenance. There is also a new PowerShell script that allows you to migrate between the different storage type options. For example from database to file-system.
- **Workflow Enhancements** - Workflow used to hide items until they reached the first major version, which led to many implementations of a "fast-forward" function to jump straight to version 1.1 vs. 0.1. The new workflow allows you to specify a workflow as "collaborative" and therefore be seen by all users. You can also optionally allow users read-only access to in-progress workflow items. You can now also assign Workflow activities to specific users, vs. only groups in the past.
- **Privileges** - It was common to have more admins that you should in current versions of the product, to give users a couple of key system-wide operations. These have been made more granular, and can be granted to individual users and groups for improved user management.
- **Content Manager Tracing** - Allows more in-depth debugging and performance analysis of CME extensions and customization, like Event System code.
- **Topology Manager UI** - Topology Manager now has a read-only UI, to visualize your setup. Configuration is still via PowerShell scripts.
- **Chinese** - the UI now includes simplified Chinese for free (previously a paid language pack)
- **Notification Framework** - allows customizations to surface notifications to the users via the notification area in the top right of the CME.

###### Content Delivery

- **Deployer** - The content deployer has been improved, to be more scalable. Before it performed two functions, receive package and deploy package. Now those two functions have be separated, drastically improving scale-ability options. The ability to deploy to multiple destinations has also been added.
- **Robustness** - Better recovery from database outages
- **Cache** - Lots of cache improvements for both Java and .NET. especially in conjunction with the Content Interaction Library (CIL)

###### Translation Manager

- **Versioning** - Send minor versions for translation
- **Automatic Publish to Preview** - An automatic publish to preview can be enabled, whenever an item is sent or retrieved for translation. This can also be filtered by type.

In the coming weeks, I'll try and dive a little deeper on a few of the more interesting improvements to see whats possible.
