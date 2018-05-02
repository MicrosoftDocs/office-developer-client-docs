---
title: "FillBkgnd Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm365
 
localization_priority: Normal
ms.assetid: 603d698f-a025-538c-8767-18e7716a9a5f
description: "Determines the color used for the background (fill) of the shape's fill pattern."
---

# FillBkgnd Cell (Fill Format Section)

Determines the color used for the background (fill) of the shape's fill pattern.
  
## Remarks

To set the color, enter a number from 0 to 23.
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB(  *r, g, b*  ), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. 
  
You can set the transparency of the background fill in the FillBkgndTrans cell. 
  
To get a reference to the FillBkgnd cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | FillBkgnd  <br/> |
   
To get a reference to the FillBkgnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowFill** <br/> |
| Cell index:  <br/> |**visFillBkgnd** <br/> |
   

