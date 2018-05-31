---
title: "CenterY Cell (Print Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1033792
 
localization_priority: Normal
ms.assetid: 7ce0bf66-dc8b-9646-7b04-50c969ecd67a
description: "Determines whether the drawing page is centered vertically on the printer page."
---

# CenterY Cell (Print Properties Section)

Determines whether the drawing page is centered vertically on the printer page. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Center the drawing page vertically on the printer page.  <br/> |
| FALSE  <br/> | Do not center the drawing page vertically on the printer page (the default).  <br/> |
   
## Remarks

By default, drawing pages are justified to the top and left of the printer page. Setting the CenterX and CenterY cells to TRUE places the drawing page in the center of the printer page (or pages when tiling is necessary). 
  
To get a reference to the CenterY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | CenterY  <br/> |
   
To get a reference to the CenterY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPrintProperties** <br/> |
| Cell index:  <br/> |**visPrintPropertiesCenterY** <br/> |
   

