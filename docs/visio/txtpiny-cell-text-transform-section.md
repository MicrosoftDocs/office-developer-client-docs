---
title: "TxtPinY Cell (Text Transform Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1045
 
ms.localizationpriority: medium
ms.assetid: 88ddf4b5-8248-8c1a-c387-09a607639d26
description: "Determines the y -coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is:"
---

# TxtPinY Cell (Text Transform Section)

Determines the  *y*  -coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is: 
  
= Height \* 0.5
  
## Remarks

To get a reference to the TxtPinY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | TxtPinY  <br/> |
   
To get a reference to the TxtPinY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowTextXForm** <br/> |
| **Cell index:**  <br/> |**visXFormPinY** <br/> |
   

