---
title: "PageBottomMargin Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60060
 
localization_priority: Normal
ms.assetid: 7a97e97c-278d-2e1e-6c4f-f5f32e2cdeb0
description: "Specifies the margin at the bottom of the printed page."
---

# PageBottomMargin Cell (Print Properties Section)

Specifies the margin at the bottom of the printed page.
  
## Remarks

This value represents physical units and is unaffected by scale or drawing units. For example, if this cell has a value of 0.5 in., this margin is 0.5 inch even if page units are feet. If units are not explicitly stated, this value defaults to page units. 
  
To get a reference to the PageBottomMargin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageBottomMargin  <br/> |
   
To get a reference to the PageBottomMargin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesBottomMargin** <br/> |
   

