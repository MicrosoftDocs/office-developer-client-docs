---
title: "LockPreview Cell (Document Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251742
 
ms.localizationpriority: medium
ms.assetid: 5a2bb1a7-e688-d32f-f231-ac6916d838a6
description: "Determines whether a preview is saved each time you save a drawing."
---

# LockPreview Cell (Document Properties Section)

Determines whether a preview is saved each time you save a drawing.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Do not save a preview each time a drawing is saved. |
| FALSE  <br/> | Save a preview each time a drawing is saved. |
   
## Remarks

To get a reference to the LockPreview cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockPreview  <br/> |
   
To get a reference to the LockPreview cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowDoc** <br/> |
| **Cell index:**  <br/> |**visDocLockPreview** <br/> |
   

