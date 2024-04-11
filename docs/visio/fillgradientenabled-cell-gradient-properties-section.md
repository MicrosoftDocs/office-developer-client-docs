---
title: "FillGradientEnabled Cell (Gradient Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 80db9c0c-13c6-47de-967f-ade6e5899f14
description: "Determines whether a fill gradient is enabled for this shape."
---

# FillGradientEnabled Cell (Gradient Properties Section)

Determines whether a fill gradient is enabled for this shape.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Gradient fill is displayed on the shape. |
|FALSE  <br/> |Gradient fills are not displayed on the shape. |

## Remarks

To get a reference to the **FillGradientEnabled** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use:
  
|**Value**|**Description**|
|:-----|:-----|
| **Cell name:**  <br/> | FillGradientEnabled  <br/> |

To get a reference to the **FillGradientEnabled** cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|**Value**|**Description**|
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowGradientProperties** <br/> |
| **Cell index:**  <br/> |**visFillGradientEnabled** <br/> |
