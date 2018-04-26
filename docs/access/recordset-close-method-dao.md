---
title: "Recordset.Close Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e76a81c6-ca0d-e310-c1dc-cbc5d6f6248b
description: "Closes an open Recordset ."
---

# Recordset.Close Method (DAO)

Closes an open **Recordset**. 
  
## Syntax

 *expression*  . **Close**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

If the **Recordset** object is already closed when you use **Close**, a run-time error occurs. 
  
If you try to close a **Connection** object while it has any open **Recordset** objects, the **Recordset** objects will be closed and any pending updates or edits will be canceled. Similarly, if you try to close a **Workspace** object while it has any open **Connection** objects, those **Connection** objects will be closed, which will close their **Recordset** objects. 
  
An alternative to the **Close** method is to set the value of an object variable to **Nothing** (  `Set dbsTemp = Nothing`).
  

