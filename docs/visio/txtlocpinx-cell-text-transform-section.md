---
title: "TxtLocPinX Cell (Text Transform Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251275
 
localization_priority: Normal
ms.assetid: cbfc4e91-10d1-d50e-3e8a-f269f7123276
description: "Determines the x -coordinate of the text block's center of rotation in relation to the origin of the text block. The default formula is:"
---

# TxtLocPinX Cell (Text Transform Section)

Determines the  *x*  -coordinate of the text block's center of rotation in relation to the origin of the text block. The default formula is: 
  
= TxtWidth \* 0.5
  
This formula evaluates to the horizontal center of the text block.
  
## Remarks

To get a reference to the TxtLocPinX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | TxtLocPinX  <br/> |
   
To get a reference to the TxtLocPinX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowTextXForm** <br/> |
| Cell index:  <br/> |**visXFormLocPinX** <br/> |
   

