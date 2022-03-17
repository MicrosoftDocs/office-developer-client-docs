---
title: "TheText Cell (Events Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1005
 
ms.localizationpriority: medium
ms.assetid: 2d63768e-afdb-4b3f-de49-f9ba69ae5391
description: "An event cell that is evaluated when a shape's text or text composition changes."
---

# TheText Cell (Events Section)

An event cell that is evaluated when a shape's text or text composition changes.
  
## Remarks

Event cells are evaluated only when the event occurs, not upon formula entry. You can use the TheText cell to trigger recalculations, for example, to recalculate the text width and height with the TEXTWIDTH( ) and TEXTHEIGHT( ) functions.
  
To get a reference to the TheText cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | TheText  <br/> |
   
To get a reference to the TheText cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowEvent** <br/> |
| **Cell index:**  <br/> |**visEvtCellTheText** <br/> |
   

