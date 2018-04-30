---
title: "Calling QueryRows for Small Tables"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 8c38bb0f-de0b-4d70-9f6d-db652445e137
description: "Last modified: July 23, 2011"
---

# Calling QueryRows for Small Tables

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
When retrieving rows from a small table, call [IMAPITable::QueryRows](imapitable-queryrows.md) instead of first building a restriction. Creating a restriction impacts performance because the provider must first create a table, find the matching rows in the original table, and then copy the rows to the new table. If the total number of rows in the table is less than 100, it is probably more effective to read all of the rows and then call [IMAPITable::FindRow](imapitable-findrow.md) to find the appropriate row. This is a particularly good strategy if this information is needed only occasionally. 
  
The proper time to use a restriction is when the restricted or filtered information will be used over a longer period of time or used frequently. For instance, if you always need a view with unread messages, then a restriction is the proper call to use.
  

