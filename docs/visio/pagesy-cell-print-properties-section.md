---
title: "PagesY Cell (Print Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033790
 
ms.localizationpriority: medium
ms.assetid: 396a0f3e-dbbb-3f5b-3c5d-f7dd454a765f
description: "Determines the number of printer pages on which to fit the drawing page vertically."
---

# PagesY Cell (Print Properties Section)

Determines the number of printer pages on which to fit the drawing page vertically. 
  
## Remarks

This value is used only when the OnPage cell is set to TRUE. 
  
To get a reference to the PagesY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | PagesY  <br/> |
   
To get a reference to the PagesY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowPrintProperties** <br/> |
| **Cell index:**  <br/> |**visPrintPropertiesPagesY** <br/> |
   

