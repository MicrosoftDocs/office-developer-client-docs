---
title: "PagesX Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60064
 
ms.localizationpriority: medium
ms.assetid: a10bf4c2-24f4-4c53-39ba-2b8cd5b50d2c
description: "Determines the number of printer pages on which to fit the drawing page horizontally."
---

# PagesX Cell (Print Properties Section)

Determines the number of printer pages on which to fit the drawing page horizontally. 
  
## Remarks

This value is used only when the OnPage cell is set to TRUE. 
  
To get a reference to the PagesX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | PagesX  <br/> |
   
To get a reference to the PagesX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPrintProperties** <br/> |
| **Cell index:**  <br/> |**visPrintPropertiesPagesX** <br/> |
   

