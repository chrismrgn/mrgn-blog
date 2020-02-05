---
title: "DD4T 2.0 Java, for ASP.Net Developers: Step 3 - Running in Tomcat and Debugging in Eclipse"
date: 2016-05-27T15:49:58.000Z
description: 
featuredpost: false
tags: 
  - DD4T 2.0 Java
  - DD4T 2.0 Java for ASP.Net Developers
  - Java
  - SDL Web (SDL Tridion)
  - SDL Web 8

---

Now the fun part, getting it to run. If you've followed [step 1](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers/) and [step 2](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-2-getting-something-building-and-debug-able/), we have everything we need now. The end is in sight...

Open up Eclipse, and lets get started:

1. Run-as "dd4t-2-java clean install"
    1. Expected Warnings (JARs not in Maven Central)
        1. \[WARNING\] The POM for com.tridion:cd\_cache:jar:8.1.1-1005 is missing, no dependency information available
        2. \[WARNING\] The POM for com.vs.ezlicrun:easylicense:jar:2.5 is missing, no dependency information available
        3. \[WARNING\] The POM for com.tridion:cd\_core:jar:8.1.0 is missing, no dependency information available
        4. \[WARNING\] The POM for com.tridion:cd\_model:jar:8.1.0 is missing, no dependency information available
    2. Install missing JARs Locally
        1. Download the following JARs to your machine, from the SDL install media
            1. cd\_model-8.1.0.jar
            2. cd\_cache-8.1.0.jar
            3. cd\_core-8.1.0.jar
            4. easylicense-2.5.jar
        2. Navigate to the folder they are stored in
            1. Execute the following
                1. mvn install:install-file -Dfile=cd\_core-8.1.0.jar -DgroupId=com.tridion -DartifactId=cd\_core -Dversion=8.1.0 -Dpackaging=jar
                2. mvn install:install-file -Dfile=cd\_cache-8.1.0.jar -DgroupId=com.tridion -DartifactId=cd\_cache -Dversion=8.1.0 -Dpackaging=jar
                3. mvn install:install-file -Dfile=cd\_model-8.1.0.jar -DgroupId=com.tridion -DartifactId=cd\_model -Dversion=8.1.0 -Dpackaging=jar
                4. mvn install:install-file -Dfile=easylicense-2.5.jar -DgroupId=com.vs.ezlicrun -DartifactId=easylicense -Dversion=2.5 -Dpackaging=jar
        3. **TODO**: **Update all references to 8.1.1 once Maven Central is updated and all the dependent POMs are updated**
2. Re-run Run-as "dd4t-2-java clean install"
    1. Project should now build successfully
3. Right click project and navigate to Maven > Update Maven Project
    1. Select OK
4. When ready to debug/run the project
    1. Check the environment you will connect to
        1. Navigate to src\\main\\resources\\WEB-INF\\classes and open cd\_client\_conf.xml
            1. Check the value of <DiscoveryService ServiceUri="http://**SERVER**:**PORT**/discovery.svc"/> for the correct environment
    2. Debug-as "dd4t-2-java debug"
        1. You maybe asked to allow in Windows Firewall
        2. Open preferred browser, and navigate to desired page e.g. [http://localhost:8080/ww/en/index.html](http://localhost:8080/ww/en/index.html)
        3. Bob's your uncle! Any configured breakpoints will now be _hit!_
