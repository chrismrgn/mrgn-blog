---
title: "Filtering (Prioritization) of the Tridion Publish Queue"
date: 2012-10-27T04:12:21.000Z
description: 
featuredpost: false
tags: 
  - SDL Tridion
  - SDL Web (SDL Tridion)

---

\[alert\]Originally Featured on Building Blocks [blog](http://blog.building-blocks.com/filtering-prioritization-of-the-tridion-publish-queue "Building Blocks Blog")\[/alert\]

Publisher filtering is often a request from clients with high volume publishing requirements and until recently had managed to evade my radar. Judging by feedback from others in the Tridion world, I am not alone. In this article, prioritization does not mean complete dominance of the publishing queue, instead it refers to the allocation of resources dedicated to a chosen item subset.

The SDL Tridion publisher, and therefore the publish queue, has very limited ability to control the order in which items are published (rendered and deployed). The only control available to you via the GUI is the ability to mark items as “High”, “Normal” or “Low” priority. In high volume situations, this is often not enough. This may cause important items to remain in the publish queue longer than desired.

On recent projects, I have been asked questions like:

- How can I prioritize the publish queue to publish items from a specific publication?
- Is it possible to make the publisher process “Live” items before “Staging” items?

The simple answer to both questions is yes and no.

## When is it no?

The answer is no in a single publisher environment. A single publisher cannot prioritize items unless you are looking to write custom code. A single publisher can only process the queue based on the standard “High,” “Normal,” or “Low” attributes. No weighting is given to any other characteristic of the item.

## When is it yes?

The answer is yes if you can increase the number of publisher instances in your environment. Publishers (rendering and deploying) can be filtered, but **not** prioritized. However, by filtering you can give chosen items more resources and therefore the illusion of prioritization. Therefore, to effectively achieve publishing prioritization, you will need multiple publishers.

To achieve prioritization you will need to configure your publishers similar to below:

- One or more publishers should be dedicated to the items you want to prioritize in your publish queue
- One or more publishers should remain available to process the entire publish queue

You can apply filters to all publisher instances, but be sure that you completely cover your item set or items not matching one of the filters will remain in the queue unpublished.

Unfiltered publishers will continue to process the queue as a whole regardless of whether the item matches another filtered publisher instance; this should be considered when analyzing the number of threads available to items outside of your filters.

Using publisher filters, you can more accurately control the number of threads dedicated to items matching the specified criteria and ensure that they make it through the publishing process as quickly as possible.

Publishers can be filtered on one or more of the following criteria (multiple values should be semicolon delimited):

- Priorities – The publish priority of the item (2-low, 4-normal, 6-high)
- Publications – The URI’s of the chosen publications
- Publication Targets – The URI’s of the chosen publication targets
- Host names – Host names of the Tridion Instances the command originated from

[![](http://mrgn.azurewebsites.net/wp-content/uploads/2012/10/Publisher-filtering11.jpg "Publisher Filtering")](http://mrgn.azurewebsites.net/wp-content/uploads/2012/10/Publisher-filtering11.jpg)

Publisher Filtering Window

Once you have configured your publishing filters, simply restart the publishing service for your changes to take effect.

## Example

Publication A contains the most important content; it contains information that needs to be published in as close to real-time as possible. For the scenarios below, items from Publication A are published on high priority to a backlogged publish queue containing many other high priority items.

### **Scenario A**

2 Publishers each with 4 rendering threads (No publisher filtering enabled)

Items in Publication A will have 0 – 8 threads available depending on other items in the queue. They will be queued with other high priority items.

Items from Publication A will have to wait until all other high priority items ahead of them in the queue have been published.

### **Scenario B**

2 Publishers each with 4 rendering threads (1 Publisher is filtered to handle only items from publication A)

Items in Publication A will have 4 – 8 threads available depending on other items in the queue.

Items from Publication A will begin publishing using 4 threads. When items from Publication A reach the front of the high priority queue, they will publish using all 8 threads.

## Summary

So when should you use publisher filtering? Publisher filtering is not the answer to all your problems, and careful consideration should be given before using it.

**Publisher filtering can help**

- Ensure that subsets of your content have a minimum dedicated publisher allocation at all times

**It cannot help**

- Fix an overwhelmed publishing infrastructure. The publisher and deployer infrastructure should match your projected publishing requirements.
- Compensate for inefficiencies in the publishing pipeline like:

- Poorly written TBB’s, Component Templates or Page Templates
- Network bottlenecks

Publisher filtering will allow you to get important content published faster and with increased priority, but should always be a part of a wider solution to streamline the entire publishing process.
