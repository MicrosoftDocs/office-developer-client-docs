---
title: "SoftEdgesSize Cell (Additional Effect Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a5cde2ca-f343-4a6e-b5d9-a1b78b3cd240
description: "Determines the size of a soft edge effect, in points from 0.00 to 100.00. If the SoftEdgesSize cell has a value of 0, the shape does not have soft edges."
---

# SoftEdgesSize Cell (Additional Effect Properties Section)

Determines the size of a soft edge effect, in points from 0.00 to 100.00. If the **SoftEdgesSize** cell has a value of 0, the shape does not have soft edges. 
  
## Remarks

To get a reference to the **SoftEdgesSize** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SoftEdgesSize  <br/> |
   
To get a reference to the **SoftEdgesSize** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowOtherEffectProperties** <br/> |
| Cell index:  <br/> |**visSoftEdgesSize** <br/> |
   

