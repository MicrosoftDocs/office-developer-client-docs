---
title: "ConLineJumpDirX Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm185
 
ms.localizationpriority: medium
ms.assetid: f0671835-8d48-907a-eca6-43953658f800
description: "Determines the line jump direction for line jumps occurring on a horizontal dynamic connector for a shape."
---

# ConLineJumpDirX Cell (Shape Layout Section)

Determines the line jump direction for line jumps occurring on a horizontal dynamic connector for a shape.
  
|**Value**|**Line jump direction**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Page default  <br/> |**visLOJumpDirXDefault** <br/> |
| 1  <br/> | Up  <br/> |**visLOJumpDirXUp** <br/> |
| 2  <br/> | Down  <br/> |**visLOJumpDirXDown** <br/> |
   
## Remarks

To set the default horizontal direction for  *all*  connector jumps on a page, use the PageLineJumpDirX cell in the Page Layout section. 
  
To get a reference to the ConLineJumpDirX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ConLineJumpDirX  <br/> |
   
To get a reference to the ConLineJumpDirX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowShapeLayout** <br/> |
| **Cell index:**  <br/> |**visSLOJumpDirX** <br/> |
   

