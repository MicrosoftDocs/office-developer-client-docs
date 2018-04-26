---
title: "Status Property (ADO Recordset)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bf3ccb36-c985-5fae-4f76-c48a0e20e6f7

---

# Status Property (ADO Recordset)

Indicates the status of the current record with respect to batch updates or other bulk operations.
  
## Return Value

Returns a sum of one or more [RecordStatusEnum](recordstatusenum.md) values. 
  
## Remarks

Use the **Status** property to see what changes are pending for records modified during batch updating. You can also use the **Status** property to view the status of records that fail during bulk operations, such as when you call the [Resync](resync-method-ado.md), [UpdateBatch](updatebatch-method-ado.md), or [CancelBatch](cancelbatch-method-ado.md) methods on a [Recordset](recordset-object-ado.md) object, or set the [Filter](filter-property-ado.md) property on a **Recordset** object to an array of bookmarks. With this property, you can determine how a given record failed and resolve it accordingly. 
  

