---
title: "ShdwOffsetX Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251373
 
ms.localizationpriority: medium
ms.assetid: 92ec9b11-f53f-a1c9-832a-6cac08aa5379
description: "Determines the distance in page units that a shape's drop shadow is offset horizontally from the shape."
---

# ShdwOffsetX Cell (Page Properties Section)

Determines the distance in page units that a shape's drop shadow is offset horizontally from the shape.
  
## Remarks

This value is set in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow). This value is independent of the scale of the drawing. If the drawing is scaled, the shadow offset remains the same. 
  
To get a reference to the ShdwOffsetX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShdwOffsetX  <br/> |
   
To get a reference to the ShdwOffsetX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageShdwOffsetX** <br/> |
   

