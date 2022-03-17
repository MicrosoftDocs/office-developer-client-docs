---
title: "QuickStyleFillColor Cell (Quick Style Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 41250e47-404c-40e7-99be-9bb8c1ed5ba2
description: "Determines which theme color that a shape's fill uses, as an integer from 0 to 7"
---

# QuickStyleFillColor Cell (Quick Style Section)

Determines which theme color that a shape's fill uses, as an integer from 0 to 7
  
|Value  <br/> |Description  <br/> |
|:-----|:-----|
|0  <br/> |The shape fill color inherits from the Dark theme color. |
|1  <br/> |The shape fill color inherits from the Light theme color. |
|2  <br/> |The shape fill color inherits from the Accent 1 theme color  <br/> |
|3  <br/> |The shape fill color inherits from the Accent 2 theme color  <br/> |
|4  <br/> |The shape fill color inherits from the Accent 3 theme color  <br/> |
|5  <br/> |The shape fill color inherits from the Accent 4 theme color  <br/> |
|6  <br/> |The shape fill color inherits from the Accent 5 theme color  <br/> |
|7  <br/> |The shape fill color inherits from the Accent 6 theme color  <br/> |
   
## Remarks

To get a reference to the **QuickStyleFillColor** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | QuickStyleFillColor  <br/> |
   
To get a reference to the **QuickStyleFillColor** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowQuickStyleProperties** <br/> |
| **Cell index:**  <br/> |**visQuickStyleFillColor** <br/> |
   

