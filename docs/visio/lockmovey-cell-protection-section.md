---
title: "LockMoveY Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm645
 
ms.localizationpriority: medium
ms.assetid: 4ed8cab4-112a-e96a-f4e3-02490a6f87fa
description: "Locks the vertical position of the shape so it cannot be moved vertically."
---

# LockMoveY Cell (Protection Section)

Locks the vertical position of the shape so it cannot be moved vertically.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Vertical position is locked.  <br/> |
| FALSE  <br/> | Vertical position is not locked.  <br/> |
   
## Remarks

To get a reference to the LockMoveY cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockMoveY  <br/> |
   
To get a reference to the LockMoveY cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockMoveY** <br/> |
   

