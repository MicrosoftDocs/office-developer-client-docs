---
title: "Working with Large Columns"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 452acccf-22fd-4450-b50f-eaa2b2c94515
description: "Last modified: July 23, 2011"
---

# Working with Large Columns

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Columns with string or binary property data can be large, possibly many thousands of bytes long. Because including one or more columns with hundreds of bytes in a view is often impractical, MAPI enables table implementers to truncate the value, most often to 255 bytes and less often to 510 bytes. Whenever possible, table implementers should include the full value of a property in a table column. The recommended alternative is to include only the first 255 bytes.
  
Clients cannot know in advance whether a table they are using truncates large columns. They should assume that a column represents a truncated property if the length of the column is either 255 or 510 bytes. If necessary, clients can directly retrieve the full value of a truncated column from the object by calling the object's [IMAPIProp::GetProps](imapiprop-getprops.md) method. 
  
Clients building restrictions with large properties should be aware that it is up to the table implementer as to how these restrictions operate. Some table implementers allow restrictions that are built with a truncated column to be based on the truncated size while others base it on the entire value. 
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

