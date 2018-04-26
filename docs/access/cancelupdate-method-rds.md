---
title: "CancelUpdate Method (RDS)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 373a3feb-125d-915a-fd56-d4b04b20db54
---

# CancelUpdate Method (RDS)

Cancels any changes made to the current or new row of a [Recordset](recordset-object-ado.md) object. 
  
## Syntax

 *DataControl*  . **CancelUpdate**
  
## Parameters

-  *DataControl* 
    
- An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object. 
    
## Remarks

The Cursor Service for OLE DB keeps both a copy of the original values and a cache of changes. When you call **CancelUpdate**, the cache of changes is reset to empty, and any bound controls are refreshed with the original data. 
  

