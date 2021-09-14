---
title: "IndFirst Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251254
 
ms.localizationpriority: medium
ms.assetid: 0f2e362a-3ace-787d-6326-b5bf707f0727

description: "Represents the distance the first line of each paragraph in the shape's text block is indented from the left indent of the paragraph. This value is independent of the scale of the drawing. If the drawing is scaled, the first line indent remains the same."
---

# IndFirst Cell (Paragraph Section)

Represents the distance the first line of each paragraph in the shape's text block is indented from the left indent of the paragraph. This value is independent of the scale of the drawing. If the drawing is scaled, the first line indent remains the same.
  
## Remarks

To get a reference to the IndFirst cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.IndFirst[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the IndFirst cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visIndentFirst** <br/> |
   

