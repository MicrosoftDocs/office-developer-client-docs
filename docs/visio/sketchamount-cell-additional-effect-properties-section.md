---
title: "SketchAmount Cell (Additional Effect Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 7c7353b7-f28e-4004-bf13-6e9714fbed37
description: "Determines the amount of distortion for a sketch effect, as an integer between 0 and 25."
---

# SketchAmount Cell (Additional Effect Properties Section)

Determines the amount of distortion for a sketch effect, as an integer between 0 and 25. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |The shape has no sketch effect applied to it. |
|1-25  <br/> |The shape has sketch distortion applied to it, where a value of 1 is the most distortion and 25 is the least. |
   
## Remarks

To get a reference to the **SketchAmount** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | SketchAmount  <br/> |
   
To get a reference to the **SketchAmount** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowOtherEffectProperties** <br/> |
| **Cell index:**  <br/> |**visSketchAmount** <br/> |
   

