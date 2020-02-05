---
title: "SDL Web 8: Promote & Demote"
date: 2015-12-07T17:20:50.000Z
description: 
featuredpost: false
tags: 
  - SDL Web
  - SDL Web (SDL Tridion)

---

If I had to rate features on the number of times I've been asked "can SDL Tridion (SDL Web) do ....." this would be right at the top of the list.

This feature solves the heartbreaking moment when you realize, I've created it all in the wrong Publication... oh and the business reason, of I'd like to share that content with more "people".

In SDL Web 8 there is now the feature to Promote and Demote content, either individually or as a batch via the API.

Below you can see the GUI to Promote and Demote items, however clicking Promote now would fail!

[![promote-demote](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote.png)](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote.png)

 

First you must Promote the Schema (dependent items) the Component needs. The GUI will fail if any dependency or BluePrint rules are broken, and will display a descriptive warning message to the user.

[![promote-demote1](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote1.png)](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote1.png)

 

If there are multiple parents (or children) you will be presented with an option to determine where you would like to Promote/Demote to

![promote-demote2](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote2.png)

Below, is an example of a fail, when I tried to Promote the Bundle containing test and test3 Components

[![promote-demote3](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote3.png)](http://67.205.159.130/wp-content/uploads/2015/12/promote-demote3.png)

Via the API, you can group and batch a Promote / Demote action, as well as specify more detailed options about failures - More details can be found in the Core Service API Reference Guide, but here is an overview of the function

OperationResultData<RepositoryLocalObjectData> Promote(string id,
                                                       string destinationRepositoryId,
                                                       OperationInstruction instruction,
                                                       ReadOptions readBackOptions)

- id: TcmUri of the item
- destinationRepositoryId: TcmUri of the target Publication
- instruction: controls how the action will execute, with two modes:
    - In **FailOnError** mode operation will be stopped before doing actual changes in DB if any error will be found.
    - In **FailOnWarning** mode operation will be stopped before doing actual changes in DB if any error or warning will be found.
- ReadOptions: standard ReadOptions object used throughout Core Service

To perform a batch Promote

TcmUri BatchPromote(IEnumerable<WeakLink> subjectLinks,
                    string destinationRepositoryId,
                    OperationInstruction instruction)

- subjectLinks: collection of TcmUri's to be moved
- destinationRepositoryId: TcmUri of the target Publication
- instruction: controls how the action will execute, with two modes:
    - In **FailOnError** mode operation will be stopped before doing actual changes in DB if any error will be found.
    - In **FailOnWarning** mode operation will be stopped before doing actual changes in DB if any error or warning will be found.
