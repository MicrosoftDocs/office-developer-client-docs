---
title: "About Restrictions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e119fa20-08b8-4c8d-93fc-56037220890d
description: "Last modified: July 23, 2011"
 
 
---

# About Restrictions

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A restriction is a way to limit the number of rows in a view to only those rows with values for columns that match specific criteria. There are many different opportunities for using restrictions with tables. Client applications can use restrictions, for example, to filter a contents table for messages sent by a particular person, to search for rows that either do not support a property or have set a property to a specific value, or to look for duplicate recipients within a message. 
  
The [IMAPITable::Restrict](imapitable-restrict.md) and [IMAPITable::FindRow](imapitable-findrow.md) methods are used to set restrictions on a table. **Restrict** applies the restriction to the table without retrieving any rows. To retrieve only those rows that meet the restriction, a subsequent call to [IMAPITable::QueryRows](imapitable-queryrows.md) or a similar method is required. **FindRow** applies the restriction and retrieves the first row in the table that matches the criteria. **FindRow** applies a temporary restriction, which is in existence only for the duration of the call, whereas **Restrict** applies a more permanent restriction. 
  
Some clients can build a restriction using columns that are not in the current column set. Supporting such a restriction is optional and table implementers that do support it add value, particularly for contents tables. Table implementers that do not support it can return the MAPI_E_TOO_COMPLEX value from a **Restrict** call or the MAPI_E_NOT_FOUND value from a **FindRow** call. 
  
Clients should be aware that, even if the provider does support restrictions on columns not in the current column set, they will get better performance overall by specifying the columns they intend to use in their restrictions with [IMAPITable::SetColumns](imapitable-setcolumns.md).
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

