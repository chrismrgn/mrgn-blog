---
title: "Stop Publishing Un-translated Content Accidentally"
date: 2016-12-09T01:16:41.000Z
description: 
featuredpost: false
tags: 
  - Event System
  - SDL Web
  - SDL Web (SDL Tridion)
  - Translation

---

In a large SDL Web (SDL Tridion) implementation, with multiple languages and countries, it is inevitable that change control will be a problem that needs to be managed.

###### Scenario

1. You don't localize pages, to keep global control over them
2. You have a central editorial team, creating content for all markets
3. Your central team creates new content, and adds it to pages
4. Your local markets publish the page before translation has been initiated or completed

###### Result

English (or master language) content on a local market website. This is not good!

###### Solutions

There are several solutions, and each have different amounts of up-front development, on-going maintenance and running budget.

Some of the solutions you'll likely consider are:

1. **Workflow** - probably the "right" solution, but requires a larger initial outlay in planning and development as well as testing and training for end users
2. **Localize** - localizing pages or components is certainly a solution, but one day you will have to go back and unlocalize to get the new content. This also begs the question, how do you know what to localize? Everything?
3. **Process** - communication and automatic notifications can be a great tool, but are only as good as the human in the process. If the human does not heed the warning, the problem will occur

All of these solutions are viable options, and with the right execution would work successfully. However I needed something quicker, and that would guarantee results. Enter option 4.

###### Another Solution

I chose to use SDL Web's Event System, and intercept publishing and determine whether or not the item being published was "valid".

There are a few things to consider when using this approach:

- **Performance** - additional load on the server
- **Resolved Items** - publishing a Component can publish more than you expect
- **Component Links** - nested component content might be output on the page
- **What is Valid** - determining if content is indeed translated
- **Exclusions** - there are always exceptions

Here are snippets from my solution, that with modification could work for your situation. Each situation is going to have different constraints, on how important or critical each factor mentioned above is.

 

###### The Event Trigger

I toyed around with a few different triggers, but ultimately found that the creation of a Publish Transaction worked best for me

EventSystem.Subscribe<PublishTransaction, SaveEventArgs>(OnPublishTransactionsCreated, EventPhases.Initiated);

###### Multiple Calls

This event fires each time SDL Web updates the Publish Transaction, including changing states between, 'waiting', 'in progress' etc. Adding a check for a default TCM Id resolved this

if (publishTransaction.Id == "tcm:0-0-0")

###### Resolved Items

As mentioned, publishing one item (especially components) can cause the publish of several. Calling the ResolveEngine you can get everything that is going to be published

var resolvedItems = ResolveEngine.ResolveItem(item, resolveInstruction, publishContext)

###### Is it Translated?

Possibly the most difficult part. In my situation I could rely on the BluePrint to determine if the content was "ready" to be published. If the content was localized in the correct Publication, then it was a'OK to publish

if (publication.Parents.Any(x => x.Title.StartsWith("041")))
   contentPublication = publication.Parents.First(x => x.Title.StartsWith("041")) as Publication;
 else if (publication.Parents.Any(x => x.Title.StartsWith("040")))
   contentPublication = publication.Parents.First(x => x.Title.StartsWith("040")) as Publication;
 else if (publication.Parents.Any(x => x.Title.StartsWith("031")))
   contentPublication = publication.Parents.First(x => x.Title.StartsWith("031")) as Publication;
 else if (publication.Parents.Any(x => x.Title.StartsWith("030")))
   contentPublication = publication.Parents.First(x => x.Title.StartsWith("030")) as Publication;
 else if (publication.Parents.Any(x => x.Title.StartsWith("020")))
   contentPublication = publication.Parents.First(x => x.Title.StartsWith("020")) as Publication;

###### Checking Each Resolved Item

This part is easy. If it is a Page, get all the Component Presentations and check each Component's owning Publication is correct. If it is a Component, just check the owning Publication. For the purpose of this example, I did not concern myself with Component Links.

private List<string> ValidatePage(Page page, Publication contentPublication)
{
   List<string> results = new List<string>();
   foreach (Component component in page.ComponentPresentations.Select(x => x.Component))
   {
      results.AddRange(ValidateComponent(component, page, contentPublication));
   }

   return results;
 }

private List<string> ValidateComponent(Component component, Page page, Publication contentPublication)
{
   List<string> results = new List<string>();

   if(component.OwningRepository.Id != contentPublication.Id)
       results.Add(string.Format("Component <b>{0} ({1})</b> is not localized at <b>{2} ({3})</b>", component.Title, component.Id, contentPublication.Title, contentPublication.Id));

   //TODO: Nested Components

   return results;
 }

###### Block Publish and Notify Users

If I get any validation messages back, then I do three things in my case

1. Throw an exception, with clear message, which is displayed to the user in the notification area
2. Delete the Publish Translation
3. Send an email with additional details, hints on how to resolve the issue and who to call if they can't resolve it themselves
