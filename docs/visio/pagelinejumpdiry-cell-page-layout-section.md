---
title: "PageLineJumpDirY Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm770
 
ms.localizationpriority: medium
ms.assetid: f73cc157-b332-279b-f7cf-d5a090bc09a4
description: "Determines the direction of line jumps on vertical dynamic connectors on the drawing page for which you haven't applied a local jump direction."
---

# PageLineJumpDirY Cell (Page Layout Section)

Determines the direction of line jumps on vertical dynamic connectors on the drawing page for which you haven't applied a local jump direction.
  
|**Value**|**Line jump direction**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Default; up or the page's setting for shapes  <br/> |**visLOJumpDirYDefault** <br/> |
| 1  <br/> | Left  <br/> |**visLOJumpDirYLeft** <br/> |
| 2  <br/> | Right  <br/> |**visLOJumpDirYRight** <br/> |
   
## Remarks

To get a reference to the PageLineJumpDirY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | PageLineJumpDirY  <br/> |
   
To get a reference to the PageLineJumpDirY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPageLayout** <br/> |
| **Cell index:**  <br/> |**visPLOJumpDirY** <br/> |
   

