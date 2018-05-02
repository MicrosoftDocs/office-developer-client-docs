---
title: "ShapeShdwOffsetX Cell (Fill Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60076
 
localization_priority: Normal
ms.assetid: a426f471-d35f-ef87-4c59-2c007ec2653f
description: "Determines the distance in page units that a shape's shadow is offset horizontally from the shape."
---

# ShapeShdwOffsetX Cell (Fill Format Section)

Determines the distance in page units that a shape's shadow is offset horizontally from the shape.
  
## Remarks

This value corresponds to the value in the **X Offset** setting in the **Shadow** dialog box (on the **Home** tab, in the **Shape** group, click **Shadow**, and then click **Shadow Options**).
  
To get a reference to the ShapeShdwOffsetX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ShapeShdwOffsetX  <br/> |
   
To get a reference to the ShapeShdwOffsetX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowFill** <br/> |
| Cell index:  <br/> |**visFillShdwOffsetX** <br/> |
   

