---
title: "Children Property (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 66eff203-68e5-a36d-eb2f-2e9faa80deb6
---

# Children Property (ADO MD)

Returns a [Members](members-collection-ado-md.md) collection for which the current [Member](member-object-ado-md.md) is the parent in the hierarchy. 
  
## Return Values

Returns a **Members** collection and is read-only. 
  
## Remarks

The **Children** property contains a **Members** collection for which the current **Member** is the hierarchical parent. Leaf level **Member** objects have no child members in the **Members** collection. This property is only supported on **Member** objects belonging to a [Level](level-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Position](position-object-ado-md.md) object. 
  

