---
title: "QuickStyleShadowColor Cell (Quick Style Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 0a80959f-941f-451c-9049-dc661ff4930f
description: "Determines which theme color that a shape's shadow uses, as an integer from 0 to 7."
---

# QuickStyleShadowColor Cell (Quick Style Section)

Determines which theme color that a shape's shadow uses, as an integer from 0 to 7.
  
|||
|:-----|:-----|
|Value  <br/> |Description  <br/> |
|0  <br/> |The shape shadow color inherits from the Dark theme color.  <br/> |
|1  <br/> |The shape shadow color inherits from the Light theme color.  <br/> |
|2  <br/> |The shape shadow color inherits from the Accent 1 theme color.  <br/> |
|3  <br/> |The shape shadow color inherits from the Accent 2 theme color.  <br/> |
|4  <br/> |The shape shadow color inherits from the Accent 3 theme color.  <br/> |
|5  <br/> |The shape shadow color inherits from the Accent 4 theme color.  <br/> |
|6  <br/> |The shape shadow color inherits from the Accent 5 theme color.  <br/> |
|7  <br/> |The shape shadow color inherits from the Accent 6 theme color.  <br/> |
   
## Remarks

To get a reference to the **QuickStyleShadowColor** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | QuickStyleShadowColor  <br/> |
   
To get a reference to the **QuickStyleShadowColor** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowQuickStyleProperties** <br/> |
| Cell index:  <br/> |**visQuickStyleShadowColor** <br/> |
   

