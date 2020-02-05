---
title: "Navigation (and other custom items) in DD4T 2 Java"
date: 2016-07-14T03:19:46.000Z
description: 
featuredpost: false
tags: 
  - DD4T
  - DD4T 2.0 Java
  - DD4T 2.0 Java for ASP.Net Developers
  - Java
  - SDL Web (SDL Tridion)
  - SDL Web 8

---

You might have noticed my recent blog posts are of a Java nature, and that's not like me. I'm currently on a Java project, so that means everything is a fun new world of learning (and pain) :)

On the project, one of the early tasks is navigation as you would expect. As I need to tackle this task soon, I started to look around the web for patterns and practices others have followed. Unfortunately I didn't really find much information on navigation in DD4T Java (there are a few posts for .Net), so I decided I'd give it a go.

Before I start, I would first like to highlight a few caveats

- I am not a seasoned Java developer. I am from a .Net background, so please don't be too harsh
- This is a pre-release view of the research (and self-learning) I have been doing in my spare time. The code will probably look quite different by the time it makes it to production on my project.

Now, lets begin

###### Why Share so Early?

I decided to share this early for two main reasons:

1. You can help me improve it
2. Others working on Navigation for DD4T 2 Java may also be looking for ideas on how to get started

###### Approach

For the approach, I decided to follow the same pattern as DD4T employs for retrieving items from SDL, using factories and data binders. It makes it a little more future proof, when things inevitably change.

So far it all seems to be working quite well, however I do still have several todo's in the code which need some attention.

###### The Contract

I'm a fan of developing to a [contract](https://en.wikipedia.org/wiki/Design_by_contract), to decouple my application tiers. So, the first step was to define a Json structure I am happy with, and make that the contract between SDL Web and my DD4T application.

The specifics of your Json contract are up to you (and your requirements), but here is a simple example

\[gist id="5a20da8d1a4f7a98788c9db93e384c9c"\]

###### The Models

Now, working from the bottom up, I needed to define models to correspond with my contract. I ended up with

\[gist id="76c81ffda80f488908c08a0eb490f9a9"\]

###### The Databinder

With the foundations in place, I needed to implement the data binding layer, to de-serialize my Json to POJOs.

\[gist id="ed1c13c3ec72e8c6a813705b8bfc2317"\]

I also added a factory, to plumb in the data binding process

\[gist id="2f6af1bd665b9d723fc1474016bdfff4"\]

###### The Factory

Keeping it plugable, next I created a factory

\[gist id="53ca833a7d65d358c497fc40ee1749db"\]

###### The Controller

I decided to go with a dedicated navigation controller

\[gist id="219443179e0ea4f5b1deb6717e94b148"\]

###### The View

The last piece of the puzzle (excluding the configuration) was the View.

For now I am outputting it via a JSP include. I plan to investigate the DD4t SmartInclude tag as an alternative.

**The include**

\[gist id="9f7d238dae2fa2467d1e0887209c669a"\]

**The View**

\[gist id="11c32e07301a208b2318ecb7b1179131"\]

###### The Configuration

With all the code in place, the last step was configuration.

**web.xml**

Add a url-pattern to your dispatcher servlet mapping

<url-pattern>/mainNavigation</url-pattern>

**dispatcher-servlet.xml**

Add the following section (replacing any x's of course)

\[gist id="3e409b00ef4a9950bf0d68bef3742325"\]

I hope this was useful, and please feel free to ask me ([tweet me](https://twitter.com/chrismrgn) as I'll see it sooner) any questions.
