---
title: "BulletSize Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033780
 
localization_priority: Normal
ms.assetid: 6ff5d07b-17e2-f6ca-1860-5d498a9ebf06

description: "Specifies the size of a bullet."
---

# BulletSize Cell (Paragraph Section)

Specifies the size of a bullet. 
  
## Remarks

This value can be specified for either predefined or custom bullets, as either a percentage or a specific value. 
  
If the value is zero (0), the bullet is the same font size as that of the first character in the paragraph. If the value is a percentage, the bullet is sized as a percentage of the font size of the first character in the paragraph. Negative numbers are treated as percentages.
  
To get a reference to the BulletSize cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.BulletFontSize[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the BulletSize cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visBulletFontSize** <br/> |
   

