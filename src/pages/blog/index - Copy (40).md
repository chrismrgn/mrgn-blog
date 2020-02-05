---
title: "Overriding Ambient Data Framework Claims with Session Footprint"
date: 2014-08-28T15:48:15.000Z
description: 
featuredpost: false
tags: 
  - Configuration
  - SDL SmartTarget
  - SDL Web (SDL Tridion)

---

On your staging website you will likely want the ability to override claims within the Ambient Data Framework, to test personalizations.

To allow Session Footprint, or any other mechanism, to override the claim values in ADF, you will need to update the "cd\_ambient\_conf.xml" file within your staging website as below:

> <Security> <!-- <RequestValidator>com.tridion.webservices.security.validator.OAuth2RequestValidator</RequestValidator> <SharedSecret>sample\_passphrase</SharedSecret> --> <!-- Ambient data framework claims forwarding is enabled for the requests coming from white listed IP addresses. --> <WhiteList> <IPAddresses> <!-- WARNING: this range should be changed as in this state accepts claims from any IP --> <Ip>0.0.0.0-255.255.255.255</Ip> <Ip>0:0:0:0:0:0:0:0-ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff</Ip> </IPAddresses> </WhiteList> <!-- Ambient data framework claims forwarding is allowed only for claims listed in this section. --> <GloballyAcceptedClaims> <Claim Uri="taf:claim:ambientdata:sessioncartridge:useragent:browser" /> <Claim Uri="taf:claim:ambientdata:footprintcartridge:acceptlanguage" /> <Claim Uri="taf:taf:claim:ambientdata:footprintcartridge:recurringvisitor" /> <Claim Uri="taf:claim:ambientdata:sessioncartridge:useragent:os" /> <Claim Uri="taf:claim:ambientdata:footprintcartridge:searchquery" /> Claim Uri="taf:claim:ambientdata:sessioncartridge:session:lifetime" /> <Claim Uri="taf:claim:ambientdata:sessioncartridge:refererdomain" /> <Claim Uri="taf:claim:ambientdata:weather:type" /> </GloballyAcceptedClaims> </Security>
