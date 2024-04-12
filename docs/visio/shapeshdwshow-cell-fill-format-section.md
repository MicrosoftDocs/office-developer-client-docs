---
title: "ShapeShdwShow Cell (Fill Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: ece6c889-9291-40ea-b55a-072acdcb8a52
description: "Determines whether the shape displays a shadow, as an integer from 0 to 2."
---

# ShapeShdwShow Cell (Fill Format Section)

Determines whether the shape displays a shadow, as an integer from 0 to 2.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Always display the shadow if a shadow is specified. The shadows for sub-shapes are not displayed. |
|1  <br/> |Do not render a shadow unless the shape does not have a parent. Use sub-shape shadows if grouped together. |
|2  <br/> |Always display a shadow if a shadow is specified. The shadows for sub-shapes are displayed. |
   
## Remarks

To get a reference to the **ShapeShdwShow** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | ShapeShdwShow  <br/> |
   
To get a reference to the **ShapeShdwShow** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowFill** <br/> |
| **Cell index:**  <br/> |**visFillShdwShow** <br/> |
   

