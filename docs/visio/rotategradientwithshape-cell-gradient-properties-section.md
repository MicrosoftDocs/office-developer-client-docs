---
title: "RotateGradientWithShape Cell (Gradient Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 6aada005-3403-4666-9779-7ccb5b83b74a
description: "Determines whether a fill gradient rotates with a shape in 2D rotation, as a boolean."
---

# RotateGradientWithShape Cell (Gradient Properties Section)

Determines whether a fill gradient rotates with a shape in 2D rotation, as a boolean.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The gradient rotates with the shape when the shape is rotated around the rotation pin. The "top" of the gradient is parallel to the rotation handle. |
|FALSE  <br/> |The gradient does not rotate with the shape when the shape is rotated around the rotation pin. The "top" of the gradient is parallel to the drawing canvas. |
   
## Remarks

To get a reference to the **RotateGradientWithShape** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | RotateGradientWithShape  <br/> |
   
To get a reference to the **RotateGradientWithShape** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowGradientProperties** <br/> |
| **Cell index:**  <br/> |**visRotateGradientWithShape** <br/> |
   

