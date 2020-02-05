---
title: "Installing SDL Web 8.5 (formerly SDL Tridion) with Azure Blob Storage for Binaries"
date: 2017-01-04T23:46:59.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)

---

Before I can start looking into the new features of SDL Web 8.5 I need to install it. So I thought I'd share the experience as part of this post. For those not so familiar with installing SDL Web or SDL Tridion it is a very simple process.

I'll be using the "[Single-machine example installation guide for SDL Web](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v5/GUID-8789A353-267D-4466-9A6D-4CF6709E4E88)" guide available in the online documentation.

 

###### Server Specifications

For my test, I'll be using a DS11\_V2 Standard configuration (2 Cores, 14GB RAM) in [Microsoft Azure Cloud](https://azure.microsoft.com), running Windows Server 2016 and SQL Server 2016 SP1 Standard Edition.

This setup could easily be reproduced in Amazon AWS or on-premise, using either a shared file-system or an Amazon S3 Bucket.

 

###### Installing the CME (GUI, Databases & Services)

Follow the basic steps in the online documentation guide, briefly:

1. **Optional:** Install Web Server Role (I like to do this before running installer, so I can remove the default website and use port 80)
2. Create MTSUser account (either locally or on your domain)
3. Create databases, based on your requirements, using the provided PowerShell scripts
4. Run installer and follow wizard steps (optional [unattended install](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v5/GUID-CE873235-5FE0-489D-A63C-B979919D8F9E) for scripted environments)

 

###### Trying Microsoft Azure Blob Storage for Binaries

A notable difference (besides the new branding) in SDL Web 8.5 is the ability to store binaries outside of the Content Manager database. This is a big benefit, as in larger implementations these images, videos and documents can really swell the database size.

To enable it follow the steps [here](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v5/GUID-C6EE81F1-DEF7-4531-89E4-28E62AFA78C9) and the outline below:

1. In the Azure Portal, create a Storage Account
2. In the Storage Account, select 'Blobs'
3. Create a new 'Container' with Access type of 'Blob'
4. Update the Tridion.ContentManager.config file, with the associated Azure Blob Storage snippets, using
    1. Container name as _blobFolder_
    2. Key from Access Keys window as _accountKey_
    3. Storage account name from Access Keys window as _accountName_
5. Restart IIS
6. Upload binaries, and begin to see them appear in your Azure Blob Storage

[![](http://www.mrgn.co/wp-content/uploads/2017/01/azure-blob-storage.png)](http://www.mrgn.co/2017/01/04/installing-sdl-web-8-5-formally-sdl-tridion-with-azure-blob-storage/azure-blob-storage/)

To explore your blob storage you can use a free Microsoft tool, [Storage Explorer](http://storageexplorer.com/), from which you can download and open the binaries in an appropriate program.

[![](http://www.mrgn.co/wp-content/uploads/2017/01/open-blob-storage-1024x564.png)](http://www.mrgn.co/2017/01/04/installing-sdl-web-8-5-formally-sdl-tridion-with-azure-blob-storage/open-blob-storage/)

In terms of what appears in the SDL Web database, the change is quite simple. The binary record still exists in the database (_ITEMS_ table), but instead of referencing a _BINARY\_ID_ (in the _BINARIES_ table) they now have a _BLOB\_ID._

[![](http://www.mrgn.co/wp-content/uploads/2017/01/database.png)](http://www.mrgn.co/2017/01/04/installing-sdl-web-8-5-formally-sdl-tridion-with-azure-blob-storage/database/)

My exploration into this new feature has been using a new, blank database. If you're upgrading there are migration scripts to move back and forth between the different storage options, as described [here](http://docs.sdl.com/LiveContent/content/en-US/SDL%20Web-v5/GUID-7CC6D578-F8A0-410E-BD3C-CE3E7BA77AD4).

One thing to note on migrations, is that SDL Web relies on the configuration in the _Tridion.ContentManager.config_ file to know where to look for binaries. When you migrate from the default database storage to one of the other options you won't have a problem, as SDL Web knows the database details (assuming it is coded as the fallback). However, if you migrate from one of the other options to any other type make sure you have the _fallbackPermanentContentStorage_ specified or you will see results like below. Adding the _fallbackPermanentContentStorage_ makes the old storage mechanism read-only, so everything still works until the migration script has executed.

[![](http://www.mrgn.co/wp-content/uploads/2017/01/change-storage.png)](http://www.mrgn.co/2017/01/04/installing-sdl-web-8-5-formally-sdl-tridion-with-azure-blob-storage/change-storage/)

I also found that I needed to restart the _SDL Web Content Manager Service Host_ service in order for changes to apply; The documentation only mentions restarting IIS.

Overall, a very simple process. I can really see this improvement being high on the list of reasons to upgrade to SDL Web 8.5 for several of my recent clients.
