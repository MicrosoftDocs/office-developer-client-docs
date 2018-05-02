---
title: "QuickStyleLineColor Cell (Quick Style Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: dcfb792f-e02a-4059-acec-a178d221097c
description: "Determines which theme color that a shape's line uses, as an integer from 0 to 7."
---

# QuickStyleLineColor Cell (Quick Style Section)

Determines which theme color that a shape's line uses, as an integer from 0 to 7.
  
|||
|:-----|:-----|
|Value  <br/> |Description  <br/> |
|0  <br/> |The shape line color inherits from the Dark theme color.  <br/> |
|1  <br/> |The shape line color inherits from the Light theme color.  <br/> |
|2  <br/> |The shape line color inherits from the Accent 1 theme color  <br/> |
|3  <br/> |The shape line color inherits from the Accent 2 theme color  <br/> |
|4  <br/> |The shape line color inherits from the Accent 3 theme color  <br/> |
|5  <br/> |The shape line color inherits from the Accent 4 theme color  <br/> |
|6  <br/> |The shape line color inherits from the Accent 5 theme color  <br/> |
|7  <br/> |The shape line color inherits from the Accent 6 theme color  <br/> |
   
## Remarks

To get a reference to the **QuickStyleLineColor** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | QuickStyleLineColor  <br/> |
   
To get a reference to the **QuickStyleLineColor** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowQuickStyleProperties** <br/> |
| Cell index:  <br/> |**visQuickStyleLineColor** <br/> |
   

