---
title: "Using a Table to Work with Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c18ed9f7-c053-4453-b0b1-06234cdfb025
description: "Last modified: July 23, 2011"
 
 
---

# Using a Table to Work with Properties

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Many properties are available both from the objects that support them and as columns on tables. Whenever possible, retrieve these properties through the table.
  
Call [IMAPITable::SetColumns](imapitable-setcolumns.md) to include all of the properties that your client needs and [IMAPITable::QueryRows](imapitable-queryrows.md) to retrieve all of the rows of the table. 
  
These two calls are usually sufficient for retrieving enough information to display to a user, and are frequently sufficient for any necessary internal processing, making a call to **OpenEntry** to open the object unnecessary. 
  
There are only two exceptions:
  
- If the property is over 255 bytes. The ** IMAPITable ** interface might not return the entire property value, instead truncating it at 255 bytes. Think about this tradeoff, though. If you are displaying this data to the user, 255 bytes may be enough for a textual field such as a comment. 
    
- If you need a specific property from a single row in a table. In this case it is unnecessary to create a table with properties that will never be used. Most of the time you will need the same properties for all rows.
    

