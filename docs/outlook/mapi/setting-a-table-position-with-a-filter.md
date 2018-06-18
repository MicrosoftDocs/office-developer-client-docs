---
title: "Setting a Table Position with a Filter"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 0d66124b-a018-4db4-b55b-a0e5ed467e14
description: "Last modified: July 23, 2011"
 
 
---

# Setting a Table Position with a Filter

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Table users can move the cursor to a row that matches a set of filter criteria. Filters can be based on a variety of guidelines such as column property values, bitmasks, or subobjects. Filters are specified in MAPI using an [SRestriction](srestriction.md) structure. 
  
 **To position a table to the first row that matches the criteria established in a restriction**
  
- Call the [IMAPITable::FindRow](imapitable-findrow.md) method. Starting with the row represented by a particular bookmark, **FindRow** searches in either a forward or backward direction to locate a row that matches the criteria specified in the restriction. **FindRow** can be useful for implementing a scroll bar that is based on character strings, instead of fractional values. For example, a client can call MAPI's implementation of **FindRow** when searching through the integrated address book to enable a user, by entering one or more characters, to locate the first name that begins with the specified characters. 
    
## See also



[MAPI Tables](mapi-tables.md)

