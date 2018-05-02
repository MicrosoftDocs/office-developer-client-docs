---
title: "Deferring Processing"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a791b95f-56ad-493a-9ba5-fb4c7dd80e89
description: "Last modified: July 23, 2011"
 
 
---

# Deferring Processing

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Pass the MAPI_DEFERRED_ERRORS flag to method calls as much as possible. Many of the MAPI method calls have been optimized to accept this flag, causing the provider to either postpone the requested task until multiple tasks can be performed at once or you can wait no longer for the results.
  
For example, if you pass MAPI_DEFERRED_ERRORS to [IMsgStore::OpenEntry](imsgstore-openentry.md) to open a folder, the opening of the folder and a possible remote call can be postponed until you make another call such as a call to the folder's **GetHierarchyTable** or **GetProps** methods. Both **GetHierarchyTable** and **GetProps** require the return of data from the service provider, a task that must be performed immediately. 
  
Another way to defer processing is simply not to make a call. By being aware of the user and when the user can perceive a drain on resources or processing time, you can determine when it makes sense to make calls. There is an opportunity to improve performance by making calls either at a time when the user will not notice or by not making them at all.
  
For example, consider the situation when you are receiving more than one notification per second from a message store that is moving a great number of messages. A progress indicator is displayed to indicate the percentage of the operation's completion. Users typically will not perceive this operation to be slow until a few seconds have passed. Therefore, if you are updating the progress indicator, do not make any changes until at least four seconds after the initiation of the move operation. This will save time in the common cases when the operation is fast and inform users in a timely manner when the operation is slow.
  

