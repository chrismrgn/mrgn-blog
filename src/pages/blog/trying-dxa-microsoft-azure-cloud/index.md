---
title: "Trying SDL DXA in the Microsoft Azure Cloud"
date: 2016-07-08T23:45:40.000Z
description: 
featuredpost: false
tags: 
  - Microsoft Azure
  - SDL DXA
  - SDL DXA
  - SDL Web
  - SDL Web (SDL Tridion)

---

Following on from [Bart's talk at Tridion Developer Summit 2016 on DXA in the cloud](https://vimeo.com/168735366), I thought that looks cool, let me give that a try.

Here's how it went.

###### Setup in Azure Cloud

The steps to create a DXA instance are pretty simple.

1. Get started from this [link](https://azure.microsoft.com/en-us/marketplace/partners/sdl/digitalxperienceaccelerator/), by clicking the "Create Web App" link.
2. Log into Azure (if you don't have an account create a free account) you'll be presented with a simple form, to configure your DXA instance [![dxa-wizard](http://67.205.159.130/wp-content/uploads/2016/07/dxa-wizard.png)](http://www.mrgn.co/2016/07/trying-dxa-microsoft-azure-cloud/dxa-wizard/)
3. Hit "Create"

That's it! In about 5 minutes you'll have a working DXA instance running on the Azure Cloud. You can see mine here: [http://mrgn-dxa.azurewebsites.net](http://mrgn-dxa.azurewebsites.net).

**Note:** I created my server in the West US data-center. The SDL Web infrastructure configured OOTB is located in Northern Europe. You'll get better performance having the DXA instance close to the SDL Web infrastructure.

###### What's running in Azure?

Thanks to the introduction of CIL (Content Interaction Library) and CDaaS (Content Delivery as a Service) in SDL Web 8, DXA is able to run in a FREE [Azure Website](https://en.wikipedia.org/wiki/Microsoft_Azure_Web_Sites). This is because the SDL Web integration is now entirely via a micro-services (hosted elsewhere). DXA, with SDL Web 8, can be a 100% standard ASP.NET (or Java) MVC application, and therefore it can easily run in the free tier on Azure.

**Note:** Currently this is not setup for the Java version. We expect a similar "quick start" for Java in the future, likely using Amazon AWS.

###### Connecting to Visual Studio and Deploying Changes

Now moving back to DXA, what can we do in Visual Studio (assuming Visual Studio 2015)

1. First things first, you need to connect the Azure Subscription you used (or created) above
2. In Server Explorer window expand the Azure node. From here you can explore all the files deployed, including logs files, configuration files etc.. [![vs-azure](http://67.205.159.130/wp-content/uploads/2016/07/vs-azure.png)](http://www.mrgn.co/2016/07/trying-dxa-microsoft-azure-cloud/vs-azure/)
3. Now its time to setup publishing and deployment, to do this you need to
    1. Set the username and password for deployment [![azure-creds](http://67.205.159.130/wp-content/uploads/2016/07/azure-creds.png)](http://www.mrgn.co/2016/07/trying-dxa-microsoft-azure-cloud/azure-creds/)
    2. Setup a deployment source (I'm going to use Local Git) [![azure-deployment-source](http://67.205.159.130/wp-content/uploads/2016/07/azure-deployment-source.png)](http://www.mrgn.co/2016/07/trying-dxa-microsoft-azure-cloud/azure-deployment-source/)
    3. Now you can clone the created Git repository on your local machine [![azure-git-repo](http://67.205.159.130/wp-content/uploads/2016/07/azure-git-repo.png)](http://www.mrgn.co/2016/07/trying-dxa-microsoft-azure-cloud/azure-git-repo/)
    4. Open the solution in Visual Studio
    5. Now you are free to remote debug, change and deploy the website all against the remote SDL Web instance provided by SDL. Pushing your changes back to the Git repository will trigger a build and deployment including your changes

If you want to point the solution to your own SDL Web instance, all you need to do is update the web.config as shown below.

**Remove**

 file="SdlSettings.config"

**Un-comment and populate**

 <!-- After Azure Web Gallery deployment, your DXA Web Application is connected to a read-only SDL Web 8 CIS environment provisioned by SDL.
 If you want to use your own CIS environment, remove the reference to SdlSettings.config above and configure below settings:
 <add key="discovery-service-uri" value="YOUR\_CIS\_DISCOVERY\_SERVICE\_URL" />
 <add key="oauth-enabled" value="true" />
 <add key="oauth-client-id" value="cduser" />
 <add key="oauth-client-secret" value="CDUserP@ssw0rd" />
 -->

**Note:** DXA must be installed, configured and published on the Content Manager side before you will see anything if you point to your own SDL Web instance.

Hopefully this helps map out the steps to accompany the great video by Bart.
