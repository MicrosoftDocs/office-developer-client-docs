---
title: "NonPrinting Cell (Miscellaneous Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251321
 
ms.localizationpriority: medium
ms.assetid: 59fe0887-2092-4fad-ea38-2aba354f3b92
description: "Switches printing on and off for the selected shape."
---

# NonPrinting Cell (Miscellaneous Section)

Switches printing on and off for the selected shape.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Printing disabled, but the shape will be displayed in the drawing window. |
| FALSE  <br/> | Printing enabled. |
   
## Remarks

You can print a guide by selecting it, and then setting the value of its NonPrinting cell to FALSE.
  
To get a reference to the NonPrinting cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | NonPrinting  <br/> |
   
To get a reference to the NonPrinting cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowMisc** <br/> |
| **Cell index:**  <br/> |**visNonPrinting** <br/> |
   

