---
title: "CenterX Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60030
 
ms.localizationpriority: medium
ms.assetid: 890e2537-66a5-2863-c78d-320b42565ea7
description: "Determines whether the drawing page is centered horizontally on the printer page."
---

# CenterX Cell (Print Properties Section)

Determines whether the drawing page is centered horizontally on the printer page. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Center the drawing page horizontally on the printer page. |
| FALSE  <br/> | Do not center the drawing page horizontally on the printer page (the default). |
   
## Remarks

By default, drawing pages are justified to the top and left of the printer page. Setting the CenterX and CenterY cells to TRUE places the drawing page in the center of the printer page (or pages when tiling is necessary). 
  
To get a reference to the CenterX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | CenterX  <br/> |
   
To get a reference to the CenterX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesCenterX** <br/> |
   

