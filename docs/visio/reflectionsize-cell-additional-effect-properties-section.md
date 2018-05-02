---
title: "ReflectionSize Cell (Additional Effect Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 7dfeb78e-a0fa-4492-b35f-70b1e2975d38
description: "Determines the size of the reflection relative to the shape, as a percentage from 0.0 to 100.0%. A shape with a value of 0% in the ReflectionSize cell does not have a reflection; a value of 100% displays a complete mirror image of the shape."
---

# ReflectionSize Cell (Additional Effect Properties Section)

Determines the size of the reflection relative to the shape, as a percentage from 0.0 to 100.0%. A shape with a value of 0% in the **ReflectionSize** cell does not have a reflection; a value of 100% displays a complete mirror image of the shape. 
  
## Remarks

To get a reference to the **ReflectionSize** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ReflectionSize  <br/> |
   
To get a reference to the **ReflectionSize** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowOtherEffectProperties** <br/> |
| Cell index:  <br/> |**visReflectionSize** <br/> |
   

