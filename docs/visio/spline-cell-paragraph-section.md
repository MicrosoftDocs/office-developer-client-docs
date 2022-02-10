---
title: "SpLine Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm970
 
ms.localizationpriority: medium
ms.assetid: 84f4e5f1-7c28-9e83-8644-28d117bb10a5

description: "Determines the distance between one line of text and the next, expressed as a percentage, where 100% is the height of a text line."
---

# SpLine Cell (Paragraph Section)

Determines the distance between one line of text and the next, expressed as a percentage, where 100% is the height of a text line.
  
|**Value**|**Description**|
|:-----|:-----|
| \>0  <br/> | Absolute spacing, regardless of font size  <br/> |
| =0  <br/> | Set solid (spacing = 100% of font size)  <br/> |
| \<0  <br/> | A percentage of font size (for example, -120% yields 120% spacing)  <br/> |
   
## Remarks

To get a reference to the SpLine cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para. SpLine [  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the SpLine cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visSpaceLine** <br/> |
   

