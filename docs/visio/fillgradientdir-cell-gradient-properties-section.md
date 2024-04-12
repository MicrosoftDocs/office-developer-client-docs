---
title: "FillGradientDir Cell (Gradient Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: e8156ff1-c540-44b8-8b69-ba4d54883260
description: "Determines the direction of the fill gradient. A gradient can be linear, radial, rectangular, or follow a path."
---

# FillGradientDir Cell (Gradient Properties Section)

Determines the direction of the fill gradient. A gradient can be linear, radial, rectangular, or follow a path. 
  
> [!NOTE]
> A linear gradient is the only gradient that takes an additional angle value (as determined by **FillGradientDir** cell). All other gradient directions have preset enumerations. 
  
****

|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Linear gradient. The **FillGradientAngle** cell determines the direction of the gradient. |
|1-7  <br/> |Radial gradients. The gradient extends outwards in a circle from a central point. |
|8-12  <br/> |Rectangular gradients. The gradient extends as a directional line from an origin with a rectangular-shaped fade. |
|13  <br/> |Path gradient. |
   
## Remarks

To get a reference to the **FillGradientDir** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | FillGradientDir  <br/> |
   
To get a reference to the **FillGradientDir** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowGradientProperties** <br/> |
| **Cell index:**  <br/> |**visFillGradientDir** <br/> |
   

