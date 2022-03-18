---
title: "RotationType Cell (3-D Rotation Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: a8d5388a-8fd0-4c6e-9633-e1f03c5bef3b
description: "Determines whether the shape follows a parallel rotation, a perspective rotation, or an oblique rotation, as an integer from 0 to 6."
---

# RotationType Cell (3-D Rotation Properties Section)

Determines whether the shape follows a parallel rotation, a perspective rotation, or an oblique rotation, as an integer from 0 to 6. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |The shape does not have any rotation. |
|1  <br/> |The shape has a parallel rotation. |
|2  <br/> |The shape has a perspective rotation. |
|3  <br/> |The shape has a top left oblique rotation. |
|4  <br/> |The shape has a top right oblique rotation. |
|5  <br/> |The shape has a bottom left oblique rotation. |
|6  <br/> |The shape has a bottom right oblique rotation. |
   
## Remarks

To get a reference to the **RotationType** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |RotationType  <br/> |
   
To get a reference to the **RotationType** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRow3DRotationProperties** <br/> |
|**Cell index:**  <br/> |**visRotationType** <br/> |
   

