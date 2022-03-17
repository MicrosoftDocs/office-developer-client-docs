---
title: "ConLineJumpDirY Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251654
 
ms.localizationpriority: medium
ms.assetid: 93f82ae0-3442-fac1-9906-b84afef85f5c
description: "Determines the line jump direction for line jumps occurring on a vertical dynamic connector for a shape."
---

# ConLineJumpDirY Cell (Shape Layout Section)

Determines the line jump direction for line jumps occurring on a vertical dynamic connector for a shape.
  
|**Value**|**Line Jump Direction**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Page default  <br/> |**visLOJumpDirYDefault** <br/> |
| 1  <br/> | Left  <br/> |**visLOJumpDirYLeft** <br/> |
| 2  <br/> | Right  <br/> |**visLOJumpDirYRight** <br/> |
   
## Remarks

To set the default vertical direction for  *all*  connector jumps on a page, use the PageLineJumpDirY cell in the Page Layout section. 
  
To get a reference to the ConLineJumpDirY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ConLineJumpDirY  <br/> |
   
To get a reference to the ConLineJumpDirY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowShapeLayout** <br/> |
| **Cell index:**  <br/> |**visSLOJumpDirY** <br/> |
   

