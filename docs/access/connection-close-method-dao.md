---
title: "Connection.Close Method (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 9b1a77cb-da12-24d6-892f-a56be103d51d
description: "Closes an open Connection ."
---

# Connection.Close Method (DAO)

Closes an open **Connection**. 
  
## Syntax

 *expression*  . **Close**
  
 *expression*  A variable that represents a **Connection** object. 
  
## Remarks

If the **Recordset** object is already closed when you use **Close**, a run-time error occurs. 
  
If you try to close a **Connection** object while it has any open **Recordset** objects, the **Recordset** objects will be closed and any pending updates or edits will be canceled. Similarly, if you try to close a **Workspace** object while it has any open **Connection** objects, those **Connection** objects will be closed, which will close their **Recordset** objects. 
  
An alternative to the **Close** method is to set the value of an object variable to **Nothing** (  `Set dbsTemp = Nothing`).
  

