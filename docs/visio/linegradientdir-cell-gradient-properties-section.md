---
title: "LineGradientDir Cell (Gradient Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: c603f9a5-f887-47ce-90bb-d41ec2d1a6a1
description: "Determines the direction of the line gradient. A gradient can be linear, radial, rectangular, or follow a path."
---

# LineGradientDir Cell (Gradient Properties Section)

Determines the direction of the line gradient. A gradient can be linear, radial, rectangular, or follow a path. 
  
> [!NOTE]
> A linear gradient is the only gradient that takes an additional angle value (as determined by **LineGradientDir** cell). All other gradient directions have preset enumerations. 
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Linear gradient. The **LineGradientAngle** cell determines the direction of the gradient. |
|1-7  <br/> |Radial gradients. The gradient extends outwards in a circle from a central point. |
|8-12  <br/> |Rectangular gradients. The gradient extends as a directional line from an origin with a rectangular-shaped fade. |
|13  <br/> |Path gradient. |
   
## Remarks

To get a reference to the **LineGradientDir** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LineGradientDir  <br/> |
   
To get a reference to the **LineGradientDir** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowGradientProperties** <br/> |
| **Cell index:**  <br/> |**visLineGradientDir** <br/> |
   

