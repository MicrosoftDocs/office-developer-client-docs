---
title: "ReplaceCopyCells Cell (Change Shape Behavior Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 2f36aefd-da49-47ea-9b90-2fa1a2298849
description: "Indicates a list of cells in the ShapeSheet that are copied from an old shape to the replacement shape during a shape replacement operation."
---

# ReplaceCopyCells Cell (Change Shape Behavior Section)

Indicates a list of cells in the ShapeSheet that are copied from an old shape to the replacement shape during a shape replacement operation. 
  
## Remarks

The master shape of the replacement must contain a **DEPENDSON** function call in the **ReplaceCopyCells** cell, where each argument in the function is a reference to a cell. Those cells are copied from the old shape to the shape that results from a shape replacement operation, regardless of where they are in the ShapeSheet. 
  
Values and/or formulas that reference other cells are copied to the resulting shape. If the resulting shape does not have the referenced cell, the copied cell contains the value only. 
  
References in the **ReplaceCopyCells** cell override protection set on cells as defined in the **Protection** section and the **ReplaceLockFormat**, **ReplaceLockShapeData**, and **ReplaceLockText** cells. 
  
To get a reference to the **ReplaceCopyCells** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ReplaceCopyCells  <br/> |
   
To get a reference to the **ReplaceCopyCells** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowReplaceBehaviors** <br/> |
| **Cell index:**  <br/> |**visReplaceCopyCells** <br/> |
   

