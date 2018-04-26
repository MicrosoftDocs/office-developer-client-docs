---
title: "Parent Property (ADO MD)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 62649da7-d35f-f11f-674c-28ce95abaf20

---

# Parent Property (ADO MD)

Indicates the member that is the parent of the current member in a hierarchy.
  
## Return Values

Returns a [Member](member-object-ado-md.md) object and is read-only. 
  
## Remarks

A member that is at the top level of a hierarchy (the root) has no parent. This property is supported only on **Member** objects belonging to a [Level](level-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Position](position-object-ado-md.md) object. 
  

