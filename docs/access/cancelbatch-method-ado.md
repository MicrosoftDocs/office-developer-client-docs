---
title: "CancelBatch Method (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: be7bf073-ed0b-e24c-7ec0-b7379236782a
---

# CancelBatch Method (ADO)

Cancels a pending batch update.
  
## Syntax

 *recordset*  . **CancelBatch** * AffectRecords * 
  
## Parameters

-  *AffectRecords* 
    
- Optional. An [AffectEnum](affectenum.md) value that indicates how many records the **CancelBatch** method will affect. 
    
## Remarks

Use the **CancelBatch** method to cancel any pending updates in a [Recordset](recordset-object-ado.md) in batch update mode. If the **Recordset** is in immediate update mode, calling **CancelBatch** without **adAffectCurrent** generates an error. 
  
If you are editing the current record or are adding a new record when you call **CancelBatch**, ADO first calls the [CancelUpdate](cancelupdate-method-ado.md) method to cancel any cached changes. After that, all pending changes in the **Recordset** are canceled. 
  
It's possible that the current record will be indeterminable after a **CancelBatch** call, especially if you were in the process of adding a new record. For this reason, it is prudent to set the current record position to a known location in the **Recordset** after the **CancelBatch** call. For example, call the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) method. 
  
If the attempt to cancel the pending updates fails because of a conflict with the underlying data (for example, a record has been deleted by another user), the provider returns warnings to the [Errors](errors-collection-ado.md) collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records. Use the [Filter](filter-property-ado.md) property ( **adFilterAffectedRecords** ) and the [Status](status-property-ado-recordset.md) property to locate records with conflicts. 
  

