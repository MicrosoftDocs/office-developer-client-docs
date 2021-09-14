---
title: "TxtWidth Cell (Text Transform Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251270
 
ms.localizationpriority: medium
ms.assetid: e2215c67-25fa-1d75-9cce-f126bb8760a1
description: "Determines the width of the text block. The default formula is:"
---

# TxtWidth Cell (Text Transform Section)

Determines the width of the text block. The default formula is:
  
= Width \* 1
  
## Remarks

To get a reference to the TxtWidth cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | TxtWidth  <br/> |
   
To get a reference to the TxtWidth cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowTextXForm** <br/> |
| Cell index:  <br/> |**visXFormWidth** <br/> |
   

