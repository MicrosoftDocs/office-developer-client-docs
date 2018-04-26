---
title: "Update Resync Property--Dynamic (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0af9cfd2-8042-65c9-cec6-77d2e7a88ad9

---

# Update Resync Property--Dynamic (ADO)

Specifies whether the [UpdateBatch](updatebatch-method-ado.md) method is followed by an implicit [Resync](resync-method-ado.md) method operation, and if so, the scope of that operation. 
  
## Settings and Return Values

Sets or returns one or more of the [ADCPROP_UPDATERESYNC_ENUM](adcprop_updateresync_enum.md) values. 
  
## Remarks

The values of ADCPROP_UPDATERESYNC_ENUM may be combined, except for adResyncAll which already represents the combination of the rest of the values.
  
The constant **adResyncConflicts** stores the resync values as underlying values, but does not override pending changes. 
  
 **Update Resync** is a dynamic property appended to the [Recordset](recordset-object-ado.md) object [Properties](properties-collection-ado.md) collection when the [CursorLocation](cursorlocation-property-ado.md) property is set to **adUseClient**. 
  

