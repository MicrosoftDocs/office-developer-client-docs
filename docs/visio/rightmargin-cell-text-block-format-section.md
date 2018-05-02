---
title: "RightMargin Cell (Text Block Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251266
 
localization_priority: Normal
ms.assetid: bc8f5469-e79f-4a68-73cb-d11c938353a4
description: "Determines the distance between the right border of the text block and the text it contains. The default is 0.1 inch."
---

# RightMargin Cell (Text Block Format Section)

Determines the distance between the right border of the text block and the text it contains. The default is 0.1 inch.
  
## Remarks

This value is independent of the scale of the drawing. If the drawing is scaled, the right margin remains the same.
  
To get a reference to the RightMargin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | RightMargin  <br/> |
   
To get a reference to the RightMargin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowText** <br/> |
| Cell index:  <br/> |**visTxtBlkRightMargin** <br/> |
   

