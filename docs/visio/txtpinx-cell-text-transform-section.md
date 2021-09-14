---
title: "TxtPinX Cell (Text Transform Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1040
 
ms.localizationpriority: medium
ms.assetid: d0c0fe52-6a9e-e40e-394e-83a851db55a4
description: "Determines the x -coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is:"
---

# TxtPinX Cell (Text Transform Section)

Determines the  *x*  -coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is: 
  
= Width \* 0.5
  
## Remarks

To get a reference to the TxtPinX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | TxtPinX  <br/> |
   
To get a reference to the TxtPinX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowTextXForm** <br/> |
| Cell index:  <br/> |**visXFormPinX** <br/> |
   

