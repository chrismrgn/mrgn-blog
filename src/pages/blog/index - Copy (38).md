---
title: "Installing SDL Tridion & Beating MSDTC"
date: 2013-11-14T05:15:34.000Z
description: 
featuredpost: false
tags: 
  - MS DTC
  - SDL Tridion
  - SDL Web (SDL Tridion)

---

Development environments are a cinch, no firewalls, no problem. Production on the other hand can be more challenging.

There is one part that lurks in the shadows, waiting, letting you think you are all done, and that everything is working. Then, you try to copy and paste, or delete a component. You try to create a new publication. BOOM!

New transaction cannot enlist in the specified transaction coordinator.

You have forgotten that firewall between the content management server and the database server, and MSDTC is not properly configured.

The documentation does a great job on the MSDTC settings, and telling you to open up firewall ports (default: 135, 5000-5500) here: [Changing DTC Security Settings](http://sdllivecontent.sdl.com/LiveContent/web/pub.xql?action=home&pub=SDL_Tridion_2011_SPONE&lang=en-US#addHistory=true&resource=&filename=Changing_DTC_security_settings.xml&docid=task_56E3D4B806E24984BAE1CEC212653143&inner_id=&tid=0566c768-5d77-4e1d-868d-135ac3118a4b&query=msdtc&scope=&eventType=lcContent.loadDoctask_56E3D4B806E24984BAE1CEC212653143&url=/LiveContent/web/search.xql%3Fc%3Dt%26pub%3DSDL_Tridion_2011_SPONE%26lang%3Den-US%26action%3Dsearch%26query%3Dmsdtc&sid=lcSearch.runSearch1384405285634&currentQuery=msdtc&currentScope=)

What I feel is missing is the part to limit the port range on which MSDTC can operate, to match the firewall rules, and make everything run smoothly.

Steps (content manager and database servers)

1. Open Component Services
2. Expand Component Services > Computers
3. View properties of "My Computer"
4. Navigate to the "Default Protocols" tab
5. View properties of "DCOM Protocols" "Connection-oriented TCP/IP" (attached)
6. Add port range (default: 5000-5500)
7. Restart distributed transaction windows service (sometimes, full server restart required)

[![image001](http://67.205.159.130/wp-content/uploads/2013/11/image001.png)](http://www.mrgn.co/2013/11/installing-sdl-tridion-beating-msdtc/image001/)
