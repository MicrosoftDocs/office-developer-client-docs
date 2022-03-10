---
title: "FillForegnd Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251241
 
ms.localizationpriority: medium
ms.assetid: 7548a480-4dce-45e0-281b-f6f8bdf05c0b
description: "Determines the color used for the foreground (stroke) of the shape's fill pattern."
---

# FillForegnd Cell (Fill Format Section)

Determines the color used for the foreground (stroke) of the shape's fill pattern.
  
## Remarks

To set the color, enter a number from 0 to 23.
  
To enter a custom color, use the RGB or HSL function. The value of a custom color is its RGB color, and RGB( *r, g, b*), rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 24 and above. 
  
You can set the transparency of the foreground fill in the FillForegndTrans cell.
  
To get a reference to the FillForegnd cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |FillForegnd  <br/> |
   
To get a reference to the FillForegnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowFill** <br/> |
|**Cell index:**  <br/> |**visFillForegnd** <br/> |
   

