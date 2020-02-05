---
title: "Mapping Ambient Data Framework Claims to SDL SmartTarget"
date: 2014-08-28T15:50:45.000Z
description: 
featuredpost: false
tags: 
  - Configuration
  - SDL SmartTarget

---

Configure which claims to send to SmartTarget/FredHopper, and the mapping of Ambient Data Framework (ADF) claim keys to SmartTarget/FredHopper Trigger keys.

Update the following section "smarttarget\_conf.xml" in your content delivery website.

> <!-- Ambient Data Framework prefixes (changes the long claim URIs of the framework into the shorter prefixes used in trigger-types.xml)--> <AmbientData> <Prefixes> <taf\_claim\_audiencemanager\_contact>am</taf\_claim\_audiencemanager\_contact> <taf\_claim\_audiencemanager\_contact\_extendeddetail>am\_ex</taf\_claim\_audiencemanager\_contact\_extendeddetail> <taf\_claim\_ambientdata\_sessioncartridge>sc</taf\_claim\_ambientdata\_sessioncartridge> <taf\_claim\_ambientdata\_sessioncartridge\_session>sc\_session</taf\_claim\_ambientdata\_sessioncartridge\_session> <taf\_claim\_ambientdata\_sessioncartridge\_useragent>sc\_ua</taf\_claim\_ambientdata\_sessioncartridge\_useragent> <taf\_claim\_ambientdata\_sessioncartridge\_useragent\_browser>sc\_ua\_browser</taf\_claim\_ambientdata\_sessioncartridge\_useragent\_browser> <taf\_claim\_ambientdata\_sessioncartridge\_useragent\_os>sc\_ua\_os</taf\_claim\_ambientdata\_sessioncartridge\_useragent\_os> <taf\_claim\_ambientdata\_sessioncartridge\_authorization>sc\_auth</taf\_claim\_ambientdata\_sessioncartridge\_authorization> <taf\_claim\_ambientdata\_weather>weather</taf\_claim\_ambientdata\_weather> </Prefixes> <!-- Add SmartTarget data to the ClaimStore, so that other systems, like the Online Marketing Explorer, can use this information --> <AddSmartTargetDataToClaimStore>true</AddSmartTargetDataToClaimStore> </AmbientData>
