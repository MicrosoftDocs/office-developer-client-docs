---
title: "SpAfter Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm960
 
ms.localizationpriority: medium
ms.assetid: 2dd56ae5-300e-ba09-a73a-83c2b6c2a0ef

description: "Determines the amount of space inserted after each paragraph in the shape's text block, in addition to any space from the SpLine cell and, if it is the last paragraph in a text block, the BottomMargin cell."
---

# SpAfter Cell (Paragraph Section)

Determines the amount of space inserted after each paragraph in the shape's text block, in addition to any space from the SpLine cell and, if it is the last paragraph in a text block, the BottomMargin cell.
  
## Remarks

This value is independent of the scale of the drawing. If the drawing is scaled, the Space After setting remains the same.
  
To get a reference to the SpAfter cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Para.SpAfter[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the SpAfter cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionParagraph** <br/> |
| **Row index:**  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visSpaceAfter** <br/> |
   

