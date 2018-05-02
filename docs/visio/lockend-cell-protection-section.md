---
title: "LockEnd Cell (Protection Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm620
 
localization_priority: Normal
ms.assetid: e9742142-4d34-1ba9-480e-d1ecff4fc7cd
description: "Locks the endpoint (EndX, EndY) of a 1-D shape to a specific location."
---

# LockEnd Cell (Protection Section)

Locks the endpoint (EndX, EndY) of a 1-D shape to a specific location.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Endpoint is locked.  <br/> |
| FALSE  <br/> | Endpoint is not locked.  <br/> |
   
## Remarks

To get a reference to the LockEnd cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockEnd  <br/> |
   
To get a reference to the LockEnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockEnd** <br/> |
   

