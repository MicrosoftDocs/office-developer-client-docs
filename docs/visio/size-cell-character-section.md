---
title: "Size Cell (Character Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251252
 
ms.localizationpriority: medium
ms.assetid: a61b50fe-eacb-b3d4-0e4e-ab3e7c972ee9

description: "Determines the size of the text in the shape's text block."
---

# Size Cell (Character Section)

Determines the size of the text in the shape's text block.
  
## Remarks

The text's size is independent of the scale of the drawing. If the drawing is scaled, the text size remains the same.
  
To get a reference to the Size cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Char.Size[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Size cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionCharacter** <br/> |
| **Row index:**  <br/> |**visRowCharacter** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visCharacterSize** <br/> |
   

