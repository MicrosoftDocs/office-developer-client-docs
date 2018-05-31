---
title: "Getting and setting multiple properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 29b7f5f1-afc1-45d9-8867-9312c072e74b
description: "Last modified: July 23, 2011"
---

# Getting and setting multiple properties

**Applies to**: Outlook 
  
By getting and setting as many properties as possible with the least number of calls, remote activity is curtailed and the overhead involved with each property is reduced. Although service providers try to collect properties before making a remote procedure call for retrieval or modification, you can optimize this effort by requesting multiple properties to begin with.
  
For example, if you work with routing lists that describe future recipients with named properties belonging to particular property sets, process all of the recipients with two calls. Use one call to [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to retrieve the identifiers for all of the recipient properties and the other call to [IMAPIProp::GetProps](imapiprop-getprops.md) to retrieve all of the values. The alternative, making a call to **GetIDsFromNames** followed by a call to **GetProps** for each recipient, is much less efficient. 
  

