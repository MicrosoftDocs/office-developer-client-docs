---
title: "BottomMargin Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm120
 
localization_priority: Normal
ms.assetid: 3121911b-34d5-d99c-3806-76f6e2824f92
description: "Determines the distance between the bottom border of the text block and the last line of text it contains. The default is 0.1 inch. This value is independent of the scale of the drawing. If the drawing is scaled, the bottom margin remains the same."
---

# BottomMargin Cell (Text Block Format Section)

Determines the distance between the bottom border of the text block and the last line of text it contains. The default is 0.1 inch. This value is independent of the scale of the drawing. If the drawing is scaled, the bottom margin remains the same.
  
## Remarks

To get a reference to the BottomMargin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | BottomMargin  <br/> |
   
To get a reference to the BottomMargin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowText** <br/> |
| Cell index:  <br/> |**visTxtBlkBottomMargin** <br/> |
   

