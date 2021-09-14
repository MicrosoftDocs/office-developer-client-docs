---
title: "QuickStyleFontColor Cell (Quick Style Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 31c56d08-19ea-4b8b-8be7-42e1c736fbca
description: "Determines the font color from the Quick Styles that a shape's text inherits from the active theme, as an integer from 0-1."
---

# QuickStyleFontColor Cell (Quick Style Section)

Determines the font color from the Quick Styles that a shape's text inherits from the active theme, as an integer from 0-1. 
  
|||
|:-----|:-----|
|Value  <br/> |Description  <br/> |
|0  <br/> |The shape text uses the Dark font color.  <br/> |
|1  <br/> |The shape text uses the Light font color.  <br/> |
   
## Remarks

To get a reference to the **QuickStyleFontColor** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | QuickStyleFontColor  <br/> |
   
To get a reference to the **QuickStyleFontColor** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowQuickStyleProperties** <br/> |
| Cell index:  <br/> |**visQuickStyleFontColor** <br/> |
   

