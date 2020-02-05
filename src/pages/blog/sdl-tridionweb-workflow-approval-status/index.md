---
title: "SDL Tridion/Web Workflow & Approval Status"
date: 2015-12-04T21:43:09.000Z
description: 
featuredpost: false
tags: 
  - SDL Tridion
  - SDL Web
  - SDL Web (SDL Tridion)
  - Workflow
  - Workflow

---

Recently I've been working with SDL Tridion Workflow and Approval status, to restrict the publishing to the live website. I've been reading other community blog posts,  including Dom's http://www.dominic.cronin.nl/weblog/what-should-we-hope-for-tridion-workflow, and for Approval Status' things have changed a little in recent versions.

## What is Approval Status

Approval status was a "Metadata" that could be assigned to any publishable item, originally to help indicate control its publishing during Workflow, but more recently at all times. At the beginning the Approval Status of an item could only be set during a Workflow process.

## What is Minimum Approval Status

Minimum Approval Status is a restriction that can be placed on a Publication Target, meaning that only items with a greater Approval Status can be published to the target.

## Before SDL Tridion 2013 SP1

Pre SDL Tridion 2013 SP1, the situation is as Dom explains. Publication Targets can and would observe the Minimum Approval Status to allow publishing only if an item was currently within a Workflow (either itself or as part of a bundle). If an item was outside of Workflow, the Minimum Approval Status restriction on the Publication Target was ignored, and items would publish successfully.

## SDL Tridion 2013 SP1

In SDL Tridion 2013 SP1, an enhancement was made to always observe the Minimum approval status restriction, regardless of whether the item was in a Workflow or not. However, there is an exception. If the item never had an Approval Status set (i.e. Approval Status value was undefined), then the Minimum Approval Status on a Publication target was ignored.

## SDL Web 8

In SDL Web 8, the Publish Targets adhere to the same rules (items with undefined Approval Status are always allowed to publish). What has changed is the way you can set Approval Status. It is now available via the Core Service API, which makes it much more useful as an easy way to restrict publishing to targets. For example, my use-case, Pages are created over a two week period. There is no official approval (hence no Workflow) but the global content editor does want the ability to "release" the change to markets once complete. The use of just Approval Status (without Workflow) will allow the basic process to be achieved easily.
