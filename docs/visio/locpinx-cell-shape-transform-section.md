---
title: "LocPinX Cell (Shape Transform Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm680
 
localization_priority: Normal
ms.assetid: b82feade-5793-8a6e-3ff4-69a4cbdd2cf9
description: "Represents the x -coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinX is:"
---

# LocPinX Cell (Shape Transform Section)

Represents the  *x*  -coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinX is: 
  
= Width \* 0.5
  
## Remarks

To get a reference to the LocPinX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LocPinX  <br/> |
   
To get a reference to the LocPinX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowXFormOut** <br/> |
| Cell index:  <br/> |**visXFormLocPinX** <br/> |
   

