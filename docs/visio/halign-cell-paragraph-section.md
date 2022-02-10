---
title: "HAlign Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm425
 
ms.localizationpriority: medium
ms.assetid: a8d6b622-60b3-e43f-b6a1-55db561204ed

description: "Determines the horizontal alignment of text in the shape's text block."
---

# HAlign Cell (Paragraph Section)

Determines the horizontal alignment of text in the shape's text block.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Left align  <br/> |**visHorzLeft** <br/> |
| 1  <br/> | Center  <br/> |**visHorzCenter** <br/> |
| 2  <br/> | Right align  <br/> |**visHorzRight** <br/> |
| 3  <br/> | Justify  <br/> |**visHorzJustify** <br/> |
| 4  <br/> | Force justify  <br/> |**visHorzForce** <br/> |
   
## Remarks

Justify adds space between words in every line except the last line of the paragraph to align both the left and right sides of text with the margins.
  
Force justify justifies every line in the paragraph, including the last.
  
To get a reference to the HAlign cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.HorzAlign[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the HAlign cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visHorzAlign** <br/> |
   

