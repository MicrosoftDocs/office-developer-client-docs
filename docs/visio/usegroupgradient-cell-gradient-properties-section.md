---
title: "UseGroupGradient Cell (Gradient Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: f1dcf0ec-8b4a-4ee1-9208-b1c84e30d37b
description: "Determines whether the shape takes on a gradient when the shape is grouped together with other shapes, as a Boolean. The value of UseGroupGradient cell affects the shape fill only."
---

# UseGroupGradient Cell (Gradient Properties Section)

Determines whether the shape takes on a gradient when the shape is grouped together with other shapes, as a Boolean. The value of **UseGroupGradient** cell affects the shape fill only. 
  
## Remarks

To get a reference to the **UseGroupGradient** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | UseGroupGradient  <br/> |
   
To get a reference to the **UseGroupGradient** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowGradientProperties** <br/> |
| Cell index:  <br/> |**visUseGroupGradient ** <br/> |
   

