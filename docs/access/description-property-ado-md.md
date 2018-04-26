---
title: "Description Property (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 06d5e1d0-6ed7-fe14-3723-3790e225482a
---

# Description Property (ADO MD)

Returns a text explanation of the current object.
  
## Return Values

Returns a **String** and is read-only. 
  
## Remarks

For [Member](member-object-ado-md.md) objects, **Description** applies only to measure and formula members. **Description** returns an empty string ("") for all other types of members. For more information about the various types of members, see the [Type](type-property-ado-md.md) property. 
  
This property is only supported on **Member** objects belonging to a [Level](level-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Position](position-object-ado-md.md) object. 
  

