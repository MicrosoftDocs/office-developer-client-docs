---
title: "PinX Cell (Shape Transform Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm790
 
ms.localizationpriority: medium
ms.assetid: dd88fb8d-3ec3-476a-870d-6642b191496f
description: "Represents the x -coordinate of the shape's pin (center of rotation) in relation to the origin of its parent."
---

# PinX Cell (Shape Transform Section)

Represents the  *x*  -coordinate of the shape's pin (center of rotation) in relation to the origin of its parent. 
  
## Remarks

To get a reference to the PinX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PinX  <br/> |
   
To get a reference to the PinX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowXFormOut** <br/> |
| Cell index:  <br/> |**visXFormPinX** <br/> |
   

