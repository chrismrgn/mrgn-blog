---
title: "Traditional vs. Dynamic Approach to SDL Web, What's the Difference?"
date: 2016-08-31T20:05:58.000Z
description: 
featuredpost: false
tags: 
  - Architecture
  - DD4T
  - dd4t
  - SDL DXA
  - SDL DXA
  - SDL Web
  - SDL Web (SDL Tridion)

---

In my role, as an SDL Web architect, I often advise customers on the application approach they should take in their implementation. One of the first bridges we normally cross, whether they are new to SDL Web or modernizing a legacy implementation, is traditional vs. dynamic. With that comes the question, what's is the difference?

Here I'll attempt to explain the difference, with some basic diagrams.

###### Traditional

The traditional approach (or at least that is how I normally describe it) is, or was, the most common way SDL Web was/is implemented. I say most common, because with SDL Web there are a million ways to implement it, and every now and then I visit a client who's found a new way. Of these one million ways to implement SDL Web many are bad ideas... and will lead you down a painful road... hence the introduction of [SDL DXA](http://www.sdl.com/cxc/digital-experience/web-experience-management/digital-experience-accelerator.html) but that is another story for another time.

The traditional approach involves all assets being managed within SDL Web, with content and layout being merged at publish time. The result, as shown in the diagram is a page, ready to be served by your preferred web server. This is a very simplistic view on the traditional approach, as you'll likely be publishing dynamic pages using languages such as JSP or ASP, but the concept still stands. Markup (layout) and content are merged together in the Content Manager and pushed to the Content Delivery.

[![Traditional](http://67.205.159.130/wp-content/uploads/2016/06/Traditional.png)](http://www.mrgn.co/2016/08/traditional-vs-dynamic-approach-sdl-web-whats-difference/traditional/)

**Pros**

- Very easy for developers to update
- Little or no obstacle to quick changes e.g. development processes
- No access to application web server is required by the developer

**Cons**

- Lack of source control
- Difficult to automate any testing
- Small changes can have large deployment impact (Template used on 100 pages, on 100 websites, requires 10,000 pages to be published)
- Developers are required to have in-depth knowledge of SDL Web and its APIs
- Possible inconsistencies, when items are not republished to all website following change

###### Dynamic (DD4t / DXA) Approach

[DD4T](http://dd4t.org/), and later DXA, where developed out of necessity to combat some of the short comings of the traditional approach. They also focused on embracing modern development practices and requirements, like continuous integration, automated testing and very dynamic and contextual web experiences.

In dynamic approach the content and layout are separated, with layout deferred to the Content Delivery tier. In the Content Manager a "pointer" or hint is given, telling the Content Delivery which template to render the content with. This leaves SDL Web to-do what is it good at, Content Management and allows developers (and preferred dynamic framework) to-do what they are good at web applications.

All items are published dynamically (normally to a database) along with an XML or JSON "specification" describing the page and component structure. The web application loads the specification, interprets it, and builds the page accordingly.

[![DD4T - DXA](http://67.205.159.130/wp-content/uploads/2016/06/DD4T-DXA.png)](http://www.mrgn.co/2016/08/traditional-vs-dynamic-approach-sdl-web-whats-difference/dd4t-dxa/)

**Pros**

- Work in a dedicated IDE, with features like intellisense and package management
- Strong development practice focus, helping with continuous integration and automated testing
- Fully source controlled, making team working and rollback a breeze
- Separation of content and layout makes template changes instant across all pages and websites
- Lower threshold for new developers as they work in familiar platforms like ASP.NET MVC and Java Spring MVC
- Strong community presence, to help solve problems and share re-usable code
- Much easier to debug and profile problems, even on Production

**Cons**

- Slower deployment (depending on dev-ops processes setup)
- Requires access to application web servers
