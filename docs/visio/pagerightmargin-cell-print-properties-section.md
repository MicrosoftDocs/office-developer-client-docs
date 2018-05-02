---
title: "PageRightMargin Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60062
 
localization_priority: Normal
ms.assetid: f864c759-ed94-8ab7-d664-cc04b3ed743e
description: "Specifies the margin on the right of the printed page."
---

# PageRightMargin Cell (Print Properties Section)

Specifies the margin on the right of the printed page.
  
## Remarks

This value represents physical units and is unaffected by scale or drawing units. For example, if this cell has a value of 0.25 in., this margin is 0.25 inch even if page units are feet. If units are not explicitly stated, this value defaults to page units. 
  
To get a reference to the PageRightMargin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageRightMargin  <br/> |
   
To get a reference to the PageRightMargin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesRightMargin** <br/> |
   

