---
title: "TxtLocPinY Cell (Text Transform Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251276
 
ms.localizationpriority: medium
ms.assetid: 3f46cfcf-7eac-4a37-e782-39f4e7f8fc43
description: "Determines the y -coordinate of the text block's center of rotation relative to the origin of the text block. The default formula is:"
---

# TxtLocPinY Cell (Text Transform Section)

Determines the  *y*  -coordinate of the text block's center of rotation relative to the origin of the text block. The default formula is: 
  
= TxtHeight \* 0.5
  
## Remarks

To get a reference to the TxtLocPinY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | TxtLocPinY  <br/> |
   
To get a reference to the TxtLocPinY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowTextXForm** <br/> |
| **Cell index:**  <br/> |**visXFormLocPinY** <br/> |
   

