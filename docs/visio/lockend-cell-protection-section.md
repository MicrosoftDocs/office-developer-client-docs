---
title: "LockEnd Cell (Protection Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm620
 
ms.localizationpriority: medium
ms.assetid: e9742142-4d34-1ba9-480e-d1ecff4fc7cd
description: "Locks the endpoint (EndX, EndY) of a 1-D shape to a specific location."
---

# LockEnd Cell (Protection Section)

Locks the endpoint (EndX, EndY) of a 1-D shape to a specific location.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Endpoint is locked. |
| FALSE  <br/> | Endpoint is not locked. |
   
## Remarks

To get a reference to the LockEnd cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockEnd  <br/> |
   
To get a reference to the LockEnd cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLock** <br/> |
| **Cell index:**  <br/> |**visLockEnd** <br/> |
   

