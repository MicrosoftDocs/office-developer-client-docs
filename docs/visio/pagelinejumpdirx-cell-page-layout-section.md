---
title: "PageLineJumpDirX Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251656
 
localization_priority: Normal
ms.assetid: 77892ec7-4c6a-78a5-5af4-5b6be7709e77
description: "Determines the direction of line jumps on horizontal dynamic connectors on the drawing page for which you haven't applied a local jump direction."
---

# PageLineJumpDirX Cell (Page Layout Section)

Determines the direction of line jumps on horizontal dynamic connectors on the drawing page for which you haven't applied a local jump direction.
  
|**Value**|**Line jump direction**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Default; left or the page's setting for shapes  <br/> |**visLOJumpDirXDefault** <br/> |
| 1  <br/> | Up  <br/> |**visLOJumpDirXUp** <br/> |
| 2  <br/> | Down  <br/> |**visLOJumpDirXDown** <br/> |
   
## Remarks

To get a reference to the PageLineJumpDirX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageLineJumpDirX  <br/> |
   
To get a reference to the PageLineJumpDirX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPageLayout** <br/> |
| Cell index:  <br/> |**visPLOJumpDirX** <br/> |
   

