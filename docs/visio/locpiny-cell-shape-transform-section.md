---
title: "LocPinY Cell (Shape Transform Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm685
 
localization_priority: Normal
ms.assetid: a29c5d4e-d3d6-d984-495a-4b0b130352ef
description: "Represents the y -coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinY is:"
---

# LocPinY Cell (Shape Transform Section)

Represents the  *y*  -coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinY is: 
  
= Height \* 0.5
  
## Remarks

To get a reference to the LocPinY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LocPinY  <br/> |
   
To get a reference to the LocPinY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowXFormOut** <br/> |
| Cell index:  <br/> |**visXFormLocPinY** <br/> |
   

