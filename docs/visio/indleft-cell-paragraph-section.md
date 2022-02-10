---
title: "IndLeft Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251255
 
ms.localizationpriority: medium
ms.assetid: 31a7d0d4-4666-ddef-c5eb-4d13803e6a2f

description: "Represents the distance all lines of text in a paragraph are indented from the left margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the left indent remains the same."
---

# IndLeft Cell (Paragraph Section)

Represents the distance all lines of text in a paragraph are indented from the left margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the left indent remains the same.
  
## Remarks

To get a reference to the IndLeft cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Para.IndLeft[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the IndLeft cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionParagraph** <br/> |
| Row index:  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visIndentLeft** <br/> |
   

