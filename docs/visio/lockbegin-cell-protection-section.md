---
title: "LockBegin Cell (Protection Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm600
 
localization_priority: Normal
ms.assetid: cce34aba-caae-51ee-992e-92a490b68ea5
description: "Locks the begin point (BeginX, BeginY) of a 1-D shape to a specific location."
---

# LockBegin Cell (Protection Section)

Locks the begin point (BeginX, BeginY) of a 1-D shape to a specific location.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Begin point is locked.  <br/> |
| FALSE  <br/> | Begin is not locked.  <br/> |
   
## Remarks

To get a reference to the LockBegin cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockBegin  <br/> |
   
To get a reference to the LockBegin cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockBegin** <br/> |
   

