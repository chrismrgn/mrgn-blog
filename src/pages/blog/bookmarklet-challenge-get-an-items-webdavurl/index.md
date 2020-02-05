---
title: "Bookmarklet Challenge: Get An Items WebDavURL"
date: 2014-12-23T03:30:27.000Z
description: 
featuredpost: false
tags: 
  - bookmarklet challenge
  - SDL Tridion
  - SDL Web (SDL Tridion)

---

Skating very close to the deadline, I have put together a simple entry for the [Bookmarklet Challenge](http://meta.tridion.stackexchange.com/questions/324/the-tridion-bookmarklet-challenge). I wanted to enter, even though very rushed, for three important reasons:

1. Organizer [Dom](http://www.dominic.cronin.nl/) is on the MVP selection committee, and therefore one of the most important people in the world in late December! :)
2. It is a great idea, creating a quick toolbox of useful tools!
3. I find myself regularly looking for the WebDavUrl for Core Service applications, when I don't want to use environment specific TCMID's

So without further ado here is the link, \[xyz-ihs snippet="Bookmarklet"\] (when the alert box pop's up, press CTRL+C to copy the WebDavUrl to your clipboard).

Now the code. The code is not perfect, but it appears to do the job in both Chrome and FireFox. It needs a bit of work in IE.

\[gist id="1827bf0a5f242922f7e4"\]

I'd also like to give a mention and thank you to [Alexander Orlov (UI Beardcore](http://tridion.uibeardcore.com/ "Orlov")) for providing the advice on streamlining the code.

Next I need to remove that ugly \[setTimeout\] function
