---
title: "FlipX Cell (Shape Transform Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251197
 
ms.localizationpriority: medium
ms.assetid: 8d4f5e14-4f17-05a6-4092-5a102c9dc85f
description: "Indicates whether the shape has been flipped horizontally."
---

# FlipX Cell (Shape Transform Section)

Indicates whether the shape has been flipped horizontally.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | The shape has been flipped horizontally.  <br/> |
| FALSE  <br/> | The shape has not been flipped horizontally.  <br/> |
   
## Remarks

To get a reference to the FlipX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | FlipX  <br/> |
   
To get a reference to the FlipX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowXFormOut** <br/> |
| Cell index:  <br/> |**visXFormFlipX** <br/> |
   

