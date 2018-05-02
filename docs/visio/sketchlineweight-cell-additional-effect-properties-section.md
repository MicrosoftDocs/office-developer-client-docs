---
title: "SketchLineWeight Cell (Additional Effect Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6cb838be-1d6d-48e1-8e9e-bd126f0c2385
description: "Determines the additional thickness added to line weight as the result of a sketch effect, in points from 0 to 50. The thickness of a shape's line increases as the value of the SketchLineWeight cell increases."
---

# SketchLineWeight Cell (Additional Effect Properties Section)

Determines the additional thickness added to line weight as the result of a sketch effect, in points from 0 to 50. The thickness of a shape's line increases as the value of the **SketchLineWeight** cell increases. 
  
## Remarks

To get a reference to the **SketchLineWeight** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | SketchLineWeight  <br/> |
   
To get a reference to the **SketchLineWeight** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowOtherEffectProperties** <br/> |
| Cell index:  <br/> |**visSketchLineWeight** <br/> |
   

