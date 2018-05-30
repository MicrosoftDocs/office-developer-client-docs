---
title: "PageLeftMargin Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60061
 
localization_priority: Normal
ms.assetid: 7ecdfc37-c9d4-2fde-ed3e-be81657c24e2
description: "Specifies the margin on the left of the printed page."
---

# PageLeftMargin Cell (Print Properties Section)

Specifies the margin on the left of the printed page.
  
## Remarks

This value represents physical units and is unaffected by scale or drawing units. For example, if this cell has a value of 0.25 in., this margin is 0.25 inch even if page units are feet. If units are not explicitly stated, this value defaults to page units. 
  
To get a reference to the PageLeftMargin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageLeftMargin  <br/> |
   
To get a reference to the PageLeftMargin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesLeftMargin** <br/> |
   

