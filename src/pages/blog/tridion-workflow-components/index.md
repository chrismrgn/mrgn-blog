---
title: "SDL Tridion Workflow & Components"
date: 2016-03-07T19:10:06.000Z
description: 
featuredpost: false
tags: 
  - Event System
  - SDL Tridion
  - SDL Web (SDL Tridion)
  - Workflow
  - Workflow

---

Sending components directly into Workflow when they are saved/created is a nice way to ensure only "approved" content makes it to your website, however there is a gotcha.

When you create a new item, the item is created as version 0.X, as it has yet to be "approved" and therefore has not reached its first major version (1.0).

The problem is, editors can only add major versions to pages (as Component Presentations). In order to "approve" content it is most common that the approver will want to see the content in-context (on a page).

We could consider a few approaches, like dynamic pages and publishing the "workflow version" dynamically, or adding the Component to a page via the API (which is allowed).

However, there is an easier option. A small block of events code can easily allow you to "fast forward" the component from version 0.X to 1.X, placing the item straight back into Workflow (for "approval") and allowing editors to add to a page.

\[gist id="955b34bf757d0f7ade6c" file="ComponentSavedWorkflowEvent.cs"\]
