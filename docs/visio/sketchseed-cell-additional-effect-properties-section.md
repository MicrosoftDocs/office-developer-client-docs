---
title: "SketchSeed Cell (Additional Effect Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6f62650d-36f8-4c6e-b79f-c9c397a5954d
description: "Represents a randomization value used to determine the geometry of a sketch effect, as a positive integer. The value of the SketchSeed cell is randomly created when a sketch effect is applied to the shape."
---

# SketchSeed Cell (Additional Effect Properties Section)

Represents a randomization value used to determine the geometry of a sketch effect, as a positive integer. The value of the **SketchSeed** cell is randomly created when a sketch effect is applied to the shape. 
  
## Remarks

To get a reference to the **SketchSeed** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | SketchSeed  <br/> |
   
To get a reference to the **SketchSeed** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowOtherEffectProperties** <br/> |
| **Cell index:**  <br/> |**visSketchSeed** <br/> |
   

