---
title: "SpBefore Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm965
 
ms.localizationpriority: medium
ms.assetid: a7d5b0a1-3657-8211-f0e0-eaed588fa0bc

description: "Determines the amount of space inserted before each paragraph in the shape's text block, in addition to any space from the SpLine cell if it is the first paragraph in a text block, the TopMargin cell."
---

# SpBefore Cell (Paragraph Section)

Determines the amount of space inserted before each paragraph in the shape's text block, in addition to any space from the SpLine cell if it is the first paragraph in a text block, the TopMargin cell.
  
## Remarks

This value is independent of the scale of the drawing. If the drawing is scaled, the Space Before setting remains the same.
  
To get a reference to the SpBefore cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.SpBefore[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the SpBefore cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visSpaceBefore** <br/> |
   

