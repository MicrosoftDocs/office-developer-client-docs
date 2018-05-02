---
title: "ShapeShdwOffsetY Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60077
 
localization_priority: Normal
ms.assetid: ef200f41-7b69-1291-f9df-a7035239a033
description: "Determines the distance in page units that a shape's shadow is offset vertically from the shape."
---

# ShapeShdwOffsetY Cell (Fill Format Section)

Determines the distance in page units that a shape's shadow is offset vertically from the shape.
  
## Remarks

This value corresponds to the value in the **Y Offset** setting in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**).
  
To get a reference to the ShapeShdwOffsetY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShapeShdwOffsetY  <br/> |
   
To get a reference to the ShapeShdwOffsetY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowFill** <br/> |
| Cell index:  <br/> |**visFillShdwOffsetY** <br/> |
   

