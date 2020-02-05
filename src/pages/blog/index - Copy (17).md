---
title: "DD4T 2.0 Java, for ASP.Net Developers: Step 1 - Getting your Environment Setup"
date: 2016-05-27T15:20:26.000Z
description: 
featuredpost: false
tags: 
  - DD4T 2.0 Java
  - DD4T 2.0 Java for ASP.Net Developers
  - Java
  - SDL Web (SDL Tridion)
  - SDL Web 8

---

To .Net developers (including me), Java is the devil. It is complex, not user friendly and there are endless config files to deal with. We are use to nice GUI's and IDEs that "do it for you".

So, when I was assigned a DD4T 2.0 Java project, with SDL Web 8, my gut reaction was... run away!!! Once they'd talked me out from the desk I was hiding under, and I could avoid it no longer, I got cracking.

Also, before getting into the weeds of it, a big thanks to Raimond Kempees! He got me over a few speed bumps on the way

So here's step 1 - Getting an environment setup, and something building and debug-able

1. Install Java JDK ([http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html))
    1. Add JAVA\_HOME environment variable to point to JDK install directory [![image2016-5-25 17-45-19](http://67.205.159.130/wp-content/uploads/2016/05/image2016-5-25-17-45-19.png)](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers/image2016-5-25-17-45-19/)
2. Install Tomcat ([https://tomcat.apache.org/download-80.cgi](https://tomcat.apache.org/download-80.cgi)) - you will need this to host and debug locally
3. Run Tomcat Monitor
    1. Set startup to "manual"
    2. Stop the service (if started), we'll attach to it later from Eclipse
4. Install Maven ([https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)) - you will need this to add some JARs not available on Maven Central
    1. Add Maven bin directory path to Path Environment Variable
    2. Open command prompt and test "mvn" is recognized command (you will see error)
5. Install Eclipse (yes it would be way easier with [IntelliJ](https://www.jetbrains.com/idea/), but who needs easy...)
    1. 64bit - [https://eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-jee-mars-2-win32-x86\_64.zip](https://eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-jee-mars-2-win32-x86_64.zip)
    2. 32bit - [https://eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-jee-mars-2-win32.zip](https://eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/mars/2/eclipse-jee-mars-2-win32.zip)
6. Download SourceTree ([https://www.sourcetreeapp.com](https://www.sourcetreeapp.com/)) and/or install GIT on the command line ([https://git-scm.com](https://git-scm.com/))

That's it, the environment is ready.

On to Step 2 & 3

[http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-2-getting-setup-in-eclipse/](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-2-getting-setup-in-eclipse/)

[http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-3-running-in-tomcat-and-debugging-in-eclipse/](http://www.mrgn.co/2016/05/dd4t-2-0-java-for-asp-net-developers-step-3-running-in-tomcat-and-debugging-in-eclipse/)
