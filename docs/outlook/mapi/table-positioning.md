---
title: "Table Positioning"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a0cbbc93-8074-4e86-b660-ee7bab910587
description: "Last modified: July 23, 2011"
 
 
---

# Table Positioning

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The current position within a table is always indicated by a cursor. There is one cursor for each view of a table; its value is set by the table's implementer. When a client or service provider using the table makes a call to change the position of the table, the value of the cursor is reset. A table's position can be changed with:
  
- A bookmark.
    
- A fractional value.
    
- A filter.
    

