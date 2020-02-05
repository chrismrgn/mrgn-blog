---
title: "Getting started with SDL DXA Java"
date: 2000-01-01T00:00:00.000Z
description: 
featuredpost: false
tags: 
  - Uncategorized

---

Java seems to be my nemesis lately. Every project I am on is Java :)

In this post, I'll run through what you need to get SDL DXA Java running on your windows local machine. The guide assumes you've got a working SDL Web 8 environment with DXA installed. If you don't you could use the public read-only SDL webservice here https://cis-stg-61f5df-dev-eu-west-1-azuredemo.tridion.sdlproducts.com:8083/discovery.svc (requires hostname azurewebsites.net & port 8080)

##### Setup project

1. Download and install Java 1.8
    1. Don't forget to add / update your JAVA\_HOME and PATH environment variables
2. Download and install Maven
    1. Don't forget to add / update your M2\_HOME, MAVEN\_HOME and PATH en vironment variables
3. Download and install Tomcat (I used version 9)
4. Download and install a suitable IDE (I used IntelliJ)
5. From a command prompt run
    1. `mvn archetype:generate to get all the available archetypes [![2016-07-19 17_55_27-mvn archetype_generate](http://67.205.159.130/wp-content/uploads/2016/07/2016-07-19-17_55_27-mvn-archetype_generate.png)](http://www.mrgn.co/?attachment_id=3541)` 
    2. Filter DXA by typing DXA [![2016-07-19 17_55_48-mvn archetype_generate](http://67.205.159.130/wp-content/uploads/2016/07/2016-07-19-17_55_48-mvn-archetype_generate.png)](http://www.mrgn.co/?attachment_id=3531)
    3. Choose the DXA archetype [![2016-07-19 17_56_06-mvn archetype_generate](http://67.205.159.130/wp-content/uploads/2016/07/2016-07-19-17_56_06-mvn-archetype_generate.png)](http://www.mrgn.co/?attachment_id=3521)
    4. Choose the version of DXA adn follow the wizard to declare names etc. [![2016-07-19 17_57_10-Select Command Prompt](http://67.205.159.130/wp-content/uploads/2016/07/2016-07-19-17_57_10-Select-Command-Prompt.png)](http://www.mrgn.co/?attachment_id=3511)
    5. You'll end up with a simple project structure, with seemingly very little inside
    6. Open the project in your IDE of choice (here are the steps for IntelliJ)
        1. Import Project
        2. Navigate and select POM file
        3. Choose project type Maven
        4. Tick boxes ‘Search for project recursively’,  'Import Maven Project Automatically’, ‘Create module groups for multi-module Maven projects’, Automatically download ‘sources’ and Automatically download ‘documentation’
        5. Select profile 'web8'
        6. Select Maven project to import (there should only be one)
        7. Select Java 1.8 as your SDK
        8. Name your project
        9. Wait for the sources and documentation to download
    7. Build the project, to check you have everything correct

That's it, you know have a basic SDL DXA Java web application setup and available in your IDE

##### Setup debugging

1. In IntelliJ, click on 'Edit Configurations'
2. Add a new 'Tomcat local' server
3. In the displayed wizard
    1. Name the configuration
    2. Select a port (e.g. 8080)
    3. On the deployment tab, add the artifact 'DXA:WAR'
4. Hit debug, to test it's working

##### What next

Now you have two options

1. Work with the default views (currently compiled)
2. Create a custom Module

Here we'll explore option one.

##### Getting the views into your solution

1. Clone Git repo 'dxa-modules' from Github here https://github.com/sdl/dxa-modules.git
2. Navigate to the clone directory
3. Navigate to ..\\dxa-modules\\webapp-java\\dxa-module-core
4. Copy the 'src' folder into the root of your project
5. Now you can edit the views, and the changes will be visible after your next build

##### Getting the controllers into your solution

If you need them, you'd follow the same process as views but cloning 'dxa-web-application-java' and copying from '..\\dxa-web-application-java\\dxa-framework\\dxa-common-api'
