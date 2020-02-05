---
title: "DD4T 2.0 Java, for ASP.Net Developers: Step 2 - Getting Setup in Eclipse"
date: 2016-05-27T15:40:10.000Z
description: 
featuredpost: false
tags: 
  - DD4T 2.0 Java
  - DD4T 2.0 Java for ASP.Net Developers
  - Java
  - SDL Web (SDL Tridion)
  - SDL Web 8

---

Now you've got the environment setup in [step 1](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers/), its time to get it working... which was easier said than done... You can start with the DD4T Archetype mentioned here, https://github.com/dd4t/dd4t-2-java/wiki, but at the time of doing this it was in a bit of "DLL hell" or whatever the JAR equivalent is. As an alternative, you can use my base project available on my public BitBucket.

1. Clone the repo ([https://bitbucket.org/chrismrgn/dd4t-2-java](https://bitbucket.org/chrismrgn/dd4t-2-java)) to your local machine
2. Ensure you have your SDL Web 8 environment setup, with the DD4T bits and pieces, and you can access your Discovey Service. Especially the items on more unusual port numbers as they may be blocked by firewalls.
3. Run Eclipse
    1. Set your default workspace e.g. C:\\workspace
    2. Open Windows > Preferences > Java > Installed JREs
        1. Add previously installed JDK from the previous post
    3. Navigate to File > Import > Maven > Existing Maven Projects and import the project into Eclipse
    4. In the opened project
        1. Right click on the Project folder and navigate to Properties > Targeted Runtimes
            1. Select JDK, not JRE
        2. Right click Project and navigate to Maven > Update Project
            1. Select OK
        3. Right click POM and navigate to Maven > Select Maven Profiles (this might take a while, as it will not download sources and Javadocs)
        4. Select POM in tree
            1. Create "Run-as" Maven Build Profiles
                1. First
                    1. Name: "dd4t-2-java clean install"
                    2. Goal : "clean install -U dependency:sources package"
                    3. Profiles: "cd-8.1.1"
                2. Second
                    1. Name: "dd4t-2-java debug"
                    2. Goal : "tomcat7:run-war -U"
                    3. Profiles: "cd-8.1.1"
                3. Ensure for each the JRE is set to "Workspace Default" and the value is "JDK...." [![image2016-5-25 17-45-19](http://67.205.159.130/wp-content/uploads/2016/05/image2016-5-25-17-45-19-1.png)](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-2-getting-something-building-and-debug-able/image2016-5-25-17-45-19-2/)

On to Step 3

[http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-3-running-in-tomcat-and-debugging-in-eclipse/](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-3-running-in-tomcat-and-debugging-in-eclipse/)
