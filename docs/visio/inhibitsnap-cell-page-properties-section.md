---
title: "InhibitSnap Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251620
 
localization_priority: Normal
ms.assetid: ab9fcebc-1550-3b9e-e3b4-e8b92424390b
description: "Determines whether the shapes on a foreground page snap to other objects on the page and shapes on the background page."
---

# InhibitSnap Cell (Page Properties Section)

Determines whether the shapes on a foreground page snap to other objects on the page and shapes on the background page.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Inhibit all snapping on the page, except for snapping to the ruler and grid.  <br/> |
| FALSE  <br/> | Enable snapping.  <br/> |
   
## Remarks

To get a reference to the InhibitSnap cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | InhibitSnap  <br/> |
   
To get a reference to the InhibitSnap cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageInhibitSnap** <br/> |
   

