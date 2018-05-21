---
title: "ShdwForegnd Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251244
 
localization_priority: Normal
ms.assetid: ea153390-631d-79fd-c1ba-4c281239a24e
description: "Determines the color used for the foreground (stroke) of the shape's drop shadow fill pattern."
---

# ShdwForegnd Cell (Fill Format Section)

Determines the color used for the foreground (stroke) of the shape's drop shadow fill pattern.
  
## Remarks

To set the color, enter a number from 0 to 23, which is an index into a collection of colors.
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB( *r, g, b*), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. 
  
You can set the transparency of the foreground color of the shape's drop shadow fill pattern in the ShdwForegndTrans cell.
  
To get a reference to the ShdwForegnd cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShdwForegnd  <br/> |
   
To get a reference to the ShdwForegnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowFill** <br/> |
| Cell index:  <br/> |**visFillShdwForegnd** <br/> |
   

