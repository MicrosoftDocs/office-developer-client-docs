---
title: "D Cell (Connection Points Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm205
 
localization_priority: Normal
ms.assetid: 28b18e8d-fecf-a798-813e-c1a310002244

description: "A scratch cell that you can use for entering or testing formulas."
---

# D Cell (Connection Points Section)

A scratch cell that you can use for entering or testing formulas.
  
## Remarks

To access the D cell, right-click a row, and then click **Change Row Type** on the shortcut menu. 
  
To get a reference to the D cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Connections.D[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the D cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionConnectionPts** <br/> |
| Row index:  <br/> |**visRowConnectionPts** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCnnctD** <br/> |
   

