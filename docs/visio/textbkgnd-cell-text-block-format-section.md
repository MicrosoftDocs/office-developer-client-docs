---
title: "TextBkgnd Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251267
 
localization_priority: Normal
ms.assetid: a238bf1c-1acd-eacd-22f3-a48acaaa4549
description: "Determines the text background color for a shape."
---

# TextBkgnd Cell (Text Block Format Section)

Determines the text background color for a shape.
  
## Remarks

The TextBkgnd cell can have any value from 0 through 24, or 255. The values 0 and 255 ( *visTxtBlklOpaque*) both indicate a transparent text background. 
  
To enter a custom color, use the RGB or HSL function plus one—for example, RGB(255,127,255)+1. The value of a custom color is its RGB color, and RGB( *r, g, b*)+1, rather than a number, will be shown in the ShapeSheet window. When used in numeric operations, custom colors have values of 25 and above. 
  
You can set the transparency of the text background color in the TextBkgndTrans cell.
  
To get a reference to the TextBkgnd cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |TextBkgnd  <br/> |
   
To get a reference to the TextBkgnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowText** <br/> |
|Cell index:  <br/> |**visTxtBlkBkgnd** <br/> |
   

