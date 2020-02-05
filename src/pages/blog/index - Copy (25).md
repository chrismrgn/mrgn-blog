---
title: "How to Test or Demonstrate SDL Web Translation for Free!"
date: 2016-07-06T00:13:25.000Z
description: 
featuredpost: false
tags: 
  - Language Cloud
  - SDL Web (SDL Tridion)
  - SDL Web 8
  - Translation
  - translation manager

---

One of SDL Web's standout features, is the ease of translation. The ability to initiate translation, directly from the content management system, and it automatically be updated once translation is complete is a clear differentiator.

In this post I'll show you how to sign up for a free trial, and plumb it into SDL Web, to aid demos and proof of concept projects.

###### 1\. Sign-up for SDL's Lanugage Cloud

Pop over to https://cxc-languagecloud.sdl.com/#app=languagecloud&entry=subscription and create a free account. Once you've got your account setup, you can then select the free trial tier from the options.

[![language cloud options](http://67.205.159.130/wp-content/uploads/2016/07/language-cloud-options.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/language-cloud-options/)

###### 2\. Setup an API Key

Now head to https://cxc-languagecloud.sdl.com/#app=languagecloud&entry=integration-tools, and create a new API key, to use in your SDL Web 8 installation

[![api key](http://67.205.159.130/wp-content/uploads/2016/07/api-key.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/api-key/)

###### 3\. Create a dictionary

Navigate to https://cxc-languagecloud.sdl.com/#app=languagecloud&entry=machine-translation and create a dictionary for your project.

[![dictionary](http://67.205.159.130/wp-content/uploads/2016/07/dictionary.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/dictionary/)

###### 4\. Select your Engines

On the next tab, "Industry Engines", select the language pairs you'll be demoing

[![engines](http://67.205.159.130/wp-content/uploads/2016/07/engines.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/engines/)

###### 5\. Configure in SDL Web 8

**For this step, I am going to assume you have already installed "Translation Manager", and selected "LanguageCloud" as the source for translations**

There are two parts to configure in SDL Web, sources and targets

- Sources - What translation is based off
- Target - Where translation will go

###### 5.1. Setting up the Source

[![Translation Source](http://67.205.159.130/wp-content/uploads/2016/07/Translation-Source.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/translation-source/)

###### 5.2. Setting up the Target

[![translation target](http://67.205.159.130/wp-content/uploads/2016/07/translation-target.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/translation-target/)

###### 6\. Sending an Item for Translation

First, we need a Component to test with. Here is our test component

[![example component](http://67.205.159.130/wp-content/uploads/2016/07/example-component.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/example-component/)

###### 6.1. Push

Right clicking on the component, and selecting the Translate option will allow you to create a new Translation Job.

[![Send for Translation](http://67.205.159.130/wp-content/uploads/2016/07/Send-for-Translation.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/send-for-translation/)

###### [![translation job](http://67.205.159.130/wp-content/uploads/2016/07/translation-job.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/translation-job/)

###### 6.2. Pull

Pull translations are initiated in the exact same way as Push translations, just from the Target instead of the Source Publication.

###### 6.3. Checking Status

From the slide out menu you can access the Translation dashboard

[![translation dashboard](http://67.205.159.130/wp-content/uploads/2016/07/translation-dashboard.png)](http://www.mrgn.co/2016/07/testing-demonstrate-sdl-web-translation-free/translation-dashboard/)

###### 6.4 Result

One the translation is complete, the (in this case French) content will automatically be place in a localize component in the Target Publication, ready for publishing.
