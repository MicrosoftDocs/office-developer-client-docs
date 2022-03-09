---
title: "IndRight Cell (Paragraph Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251256
 
ms.localizationpriority: medium
ms.assetid: f0891064-95d9-ae1b-28f3-3aef1406b636

description: "Represents the distance all lines of text in a paragraph are indented from the right margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the right indent remains the same."
---

# IndRight Cell (Paragraph Section)

Represents the distance all lines of text in a paragraph are indented from the right margin of the text block. This value is independent of the scale of the drawing. If the drawing is scaled, the right indent remains the same.
  
## Remarks

To get a reference to the IndRight cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Para.IndRight[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the IndRight cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionParagraph** <br/> |
| **Row index:**  <br/> |**visRowParagraph** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visIndentRight** <br/> |
   

