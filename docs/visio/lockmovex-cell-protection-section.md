---
title: "LockMoveX Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm640
 
ms.localizationpriority: medium
ms.assetid: 48ceeeed-66ae-a81f-2aee-f0010102dfb7
description: "Locks the horizontal position of the shape so it cannot be moved horizontally."
---

# LockMoveX Cell (Protection Section)

Locks the horizontal position of the shape so it cannot be moved horizontally.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Horizontal position is locked.  <br/> |
| FALSE  <br/> | Horizontal position is not locked.  <br/> |
   
## Remarks

To get a reference to the LockMoveX cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockMoveX  <br/> |
   
To get a reference to the LockMoveX cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockMoveX** <br/> |
   

