---
title: "ThemeIndex Cell (Theme Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 21002267-1400-4398-b937-f5b289cf0ed2
description: "Stores the enumeration of the built-in Microsoft Visio theme applied to the document, as an integer. When a new theme is chosen for the document, the ThemeIndex cell for the document and all pages and shapes it contains is updated with the index of the built-in theme."
---

# ThemeIndex Cell (Theme Properties Section)

Stores the enumeration of the built-in Microsoft Visio theme applied to the document, as an integer. When a new theme is chosen for the document, the **ThemeIndex** cell for the document and all pages and shapes it contains is updated with the index of the built-in theme. 
  
## Remarks

To get a reference to the **ThemeIndex** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | ThemeIndex  <br/> |
   
To get a reference to the **ThemeIndex** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowThemeProperties** <br/> |
| Cell index:  <br/> |**visThemeIndex** <br/> |
   

