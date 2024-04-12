---
title: "SketchFillChange Cell (Additional Effect Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 939f8f90-dee5-4175-b32a-e2964eb40681
description: "Determines the amount of randomization of the shape's fill from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the SketchFillChange cell is set to 0%, the bounding geometry of a shape's fill matches the shape's geometry. If the value is 100%, the bounding geometry of the shape's fill does not follow the geometry of the shape."
---

# SketchFillChange Cell (Additional Effect Properties Section)

Determines the amount of randomization of the shape's fill from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the **SketchFillChange** cell is set to 0%, the bounding geometry of a shape's fill matches the shape's geometry. If the value is 100%, the bounding geometry of the shape's fill does not follow the geometry of the shape. 
  
## Remarks

For best results, the ideal range of values for the **SketchFillChange** cell is between 15% and 50%. A value below 15% is barely noticeable; a value greater than 50% is increasingly more randomized. 
  
To get a reference to the **SketchFillChange** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | SketchFillChange  <br/> |
   
To get a reference to the **SketchFillChange** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowOtherEffectProperties** <br/> |
| **Cell index:**  <br/> |**visSketchFillChange** <br/> |
   

