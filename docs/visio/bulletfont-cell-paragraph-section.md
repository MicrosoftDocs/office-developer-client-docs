---
title: "BulletFont Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60023
 
ms.localizationpriority: medium
ms.assetid: a75ff1f3-2f4d-89e3-108b-e16a34f5184f

description: "Represents the number of the font used to format the text when a custom bullet string is specified and the value in the Bullet cell is non-zero."
---

# BulletFont Cell (Paragraph Section)

Represents the number of the font used to format the text when a custom bullet string is specified and the value in the Bullet cell is non-zero. 
  
## Remarks

Font numbers vary according to the fonts installed on your system. If the value is 0 and there is a custom bullet string, the font used is the same as the font of the first character of the paragraph.
  
To get a reference to the BulletFont cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.BulletFont[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the BulletFont cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visBulletFont** <br/> |
   

