---
title: "TableDef.ConflictTable Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1053356
  
localization_priority: Normal
ms.assetid: 0db8b975-eb6d-19c6-cfb7-6ce01230ebe4
description: "Returns the name of a conflict table containing the database records that conflicted during the synchronization of two replicas (Microsoft Access workspaces only). Read-only String ."
---

# TableDef.ConflictTable Property (DAO)

Returns the name of a conflict table containing the database records that conflicted during the synchronization of two replicas (Microsoft Access workspaces only). Read-only **String**. 
  
## Syntax

 *expression*  . **ConflictTable**
  
 *expression*  An expression that returns a **TableDef** object. 
  
## Remarks

The return value is a **String** data type that is a zero-length string ("") if there is no conflict table or the database isn't a replica. 
  
If two users at two separate replicas each make a change to the same record in the database, the changes made by one user will fail to be applied to the other replica. Consequently, the user with the failed change must resolve the conflicts.
  
Conflicts occur at the record level, not between fields. For example, if one user changes the Address field and another updates the Phone field in the same record, then one change is rejected. Because conflicts occur at the record level, the rejection occurs even though the successful change and the rejected change are unlikely to result in a true conflict of information.
  
The synchronization mechanism handles the record conflicts by creating conflict tables, which contain the information that would have been placed in the table, if the change had been successful. You can examine these conflict tables and work through them row by row, fixing whatever is appropriate.
  
All conflict tables are named  _table__conflict, where  _table_ is the original name of the table, truncated to the maximum table name length. 
  

