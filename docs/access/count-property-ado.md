---
title: "Count Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b59f9581-ffd1-471d-44fa-3c1bb812e140
---

# Count Property (ADO)

Indicates the number of objects in a collection.
  
## Return Value

Returns a **Long** value. 
  
## Remarks

Use the **Count** property to determine how many objects are in a given collection. 
  
Because numbering for members of a collection begins with zero, you should always code loops starting with the zero member and ending with the value of the **Count** property minus 1. If you are using Microsoft Visual Basic and want to loop through the members of a collection without checking the **Count** property, use the **For** **Each...Next** command. 
  
If the **Count** property is zero, there are no objects in the collection. 
  

