---
title: "TextPosAfterBullet Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60089
 
ms.localizationpriority: medium
ms.assetid: 08958abb-9d66-5a83-dac3-4cbfd1f6d85e

description: "Represents the distance between the first line of the paragraph and the bullet."
---

# TextPosAfterBullet Cell (Paragraph Section)

Represents the distance between the first line of the paragraph and the bullet. 
  
## Remarks

This distance is added to the distance contained in the IndFirst cell, which is the default left indent. This value is independent of the scale of the drawing. 
  
To get a reference to the TextPosAfterBullet cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.TextPosAfterBullet[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the TextPosAfterBullet cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visTextPosAfterBullet** <br/> |
   

