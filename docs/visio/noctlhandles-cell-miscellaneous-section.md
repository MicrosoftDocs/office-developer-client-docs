---
title: "NoCtlHandles Cell (Miscellaneous Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251319
 
localization_priority: Normal
ms.assetid: 4345b3e5-f522-e300-307c-4f8992a3ddce
description: "Switches the display of control handles on and off for the selected shape."
---

# NoCtlHandles Cell (Miscellaneous Section)

Switches the display of control handles on and off for the selected shape.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Control handles are not displayed when a shape is selected.  <br/> |
| FALSE  <br/> | Control handles are displayed when a shape is selected.  <br/> |
   
## Remarks

To get a reference to the NoCtlHandles cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | NoCtlHandles  <br/> |
   
To get a reference to the NoCtlHandles cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowMisc** <br/> |
| Cell index:  <br/> |**visNoCtlHandles** <br/> |
   

