---
title: "TxtHeight Cell (Text Transform Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1025
 
localization_priority: Normal
ms.assetid: cfa3ecc6-61a8-506c-ba1d-b5e1f757d44f
description: "Determines the height of the text block. The default formula is:"
---

# TxtHeight Cell (Text Transform Section)

Determines the height of the text block. The default formula is:
  
= Height \* 1
  
## Remarks

To get a reference to the TxtHeight cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | TxtHeight  <br/> |
   
To get a reference to the TxtHeight cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowTextXForm** <br/> |
| Cell index:  <br/> |**visXFormHeight** <br/> |
   

