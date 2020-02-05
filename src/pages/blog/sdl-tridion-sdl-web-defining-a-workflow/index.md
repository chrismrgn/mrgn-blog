---
title: "SDL Tridion (SDL Web): Defining a Workflow"
date: 2015-12-22T19:23:55.000Z
description: 
featuredpost: false
tags: 
  - SDL Web (SDL Tridion)
  - Workflow

---

Workflow is a rarely implemented (but extremely powerful) piece of the SDL Web (SDL Tridion) solution. It allows companies to introduce governance and control to the material on their website, inline with general content editing activities.

## Why is it rarely used?

Workflow is seen as complex. All to often when talking to customers it is deemed to complex (or scary) to implement. Or worse still, it has been implemented and disabled as it caused problems.

## Why is it disabled?

Normally, the reasons are simple. It was either defined to be too strict or too complex.

## What should you consider when defining a Workflow?

- **KISS** (Keep It Simple Stupid) - it maybe an old computer science acronym but it is relevant, especially when considering Workflow. Over complicating (especially from day one) normally ends in disaster
- **Follow REAL processes** - if you don't already follow a process for content governance be extra careful when defining a Workflow. It is all too easy to build a monster!
- **Formal vs. Informal** - once you have a Workflow down on paper, analyze it. For each step think, who, what, where and when. Also consider does it need to be formal (online, and enforced by the system), or would it function better as and informal (offline between two people) step
    - **Who** - which people, or group of people
    - **What** - what do they need to do to pass the step (or return it to the previous)
    - **Where** - are they in email, the Content Manager (CME), Experience Manager (XPM) or somewhere totally different?
    - **When** - how long will it take, when will they do it, and what if they don't?
- **Resources** - even a relatively simple Workflow can add many hours of work to a persons queue. Consider the "I want to approve all content before it goes live" scenario (very common request). If 10 pages go live per day, and each page takes 10 minutes to validate, you need 100 extra minutes in a day to do that.. and those numbers are very conservative
- **Deadlock** - Single point of failure is often a problem in Workflow. Joe's off sick this week, so nothing has been approved....
- **Fast Track** - There is ALWAYS an emergency when you need to fast track the Workflow. So consider it from the start. However, be-careful, any shortcuts WILL be used by editors more often than they should.
- **Use cases** - once you have them validate them. Not just with business, but with everyday users. What the business says happens does not always actually happen
- **The spreadsheet** - 99% of the time there is a spreadsheet. Only a few people know about it, but it almost always exists. It is the "system" the team has come up with to track "workflow". Find it and study it!

I will add, the negatives are not the product. It is a case of bloated requirements and over engineering.

Hopefully I'll blog a bit more about Workflow in the coming weeks and months, including business analysis themes as well as some technical posts.

Watch this space....
