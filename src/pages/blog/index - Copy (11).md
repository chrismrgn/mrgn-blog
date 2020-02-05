---
title: "What is the best Approach to Enterprise Business Application Architecture?"
date: 2016-09-14T21:00:16.000Z
description: 
featuredpost: false
tags: 
  - Architecture
  - Architecture
  - SDL Web
  - SDL Web (SDL Tridion)

---

I spend a lot of time consulting with some of the largest, and most complex, companies in the world. Interestingly they all seem to approach things in the same way.

They work in siloed teams, create tight coupling between applications and divergent experiences for their end users.

[![existing-1](http://67.205.159.130/wp-content/uploads/2016/09/Existing-1.png)](http://www.mrgn.co/index.php/2016/09/14/3711/existing-1/)

The result of this is:

- Interdependent release schedules reducing overall agility
- Increased QA overhead, validating changes across multiple applications
- Core back office system updates or changes become almost impossible, due to the knock on effects (e.g. change PIM from supplier A to supplier B has knock effects in both the website and partner portal)
- Frustrated developers and business stakeholders, as even minor changes take too long
- Difficulty getting a single view of the customer, as customer data and trends are spread across several systems, websites and analytics accounts

###### What is the alternative?

In my opinion we should always be working against API's and web services. We should be creating loosely coupled application architectures, in which each piece of the puzzle can change and release independently of any other piece.

[![proposed](http://67.205.159.130/wp-content/uploads/2016/09/Proposed.png)](http://www.mrgn.co/index.php/2016/09/14/3711/proposed/)

In this approach

- Each team can innovate quickly and therefore ultimately better serve the end user
- Systems are "hot swappable" with little/no impact on the public website
- API's can be exposed to many systems (internal and external) to create consistent web experiences (mobile app reports user preferences that can be replicated on the desktop)
- Versioned API's allow legacy systems to continue working whilst not limiting new initiatives
- Specialized development teams vs. enforced silos = happier developers

Most frequently I work with the [SDL Web (SDL Tridion)](http://www.sdl.com/cxc/digital-experience/web-experience-management/) Content Management System, which in recent releases has headed in this direction. It exposes Content Delivery as a Service (CDaaS) so it can be plugged into a web application with little dependency. CDaaS is a collection of micro-services which allow consumers to access content (and other SDL Web Content Delivery assets) via a set of RESTful web services.

Following writing the post, I was pointed to an article by [Martin Fowler](https://twitter.com/martinfowler) on a similar topic which is worth a read: [http://martinfowler.com/bliki/BranchByAbstraction.html](http://martinfowler.com/bliki/BranchByAbstraction.html)
