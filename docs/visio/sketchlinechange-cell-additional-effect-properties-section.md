---
title: "SketchLineChange Cell (Additional Effect Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 39192535-b55b-4c49-b63f-edb542c7a2e5
description: "Determines the amount of randomization of the shape's line from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the SketchLineChange cell is set to 0%, the geometry of the shape's line matches the shape's geometry. If the value is 100%, the geometry of the shape's line does not follow the geometry of the shape."
---

# SketchLineChange Cell (Additional Effect Properties Section)

Determines the amount of randomization of the shape's line from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the **SketchLineChange** cell is set to 0%, the geometry of the shape's line matches the shape's geometry. If the value is 100%, the geometry of the shape's line does not follow the geometry of the shape. 
  
## Remarks

For best results, the ideal range of values for the **SketchLineChange** cell is between 15% and 50%. A value below 15% is barely noticeable; a value greater than 50% could randomize the line too much. 
  
To get a reference to the **SketchLineChange** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | SketchLineChange  <br/> |
   
To get a reference to the **SketchLineChange** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowOtherEffectProperties** <br/> |
| **Cell index:**  <br/> |**visSketchLineChange** <br/> |
   

