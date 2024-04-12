---
title: "LockCrop Cell (Protection Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm610
 
ms.localizationpriority: medium
ms.assetid: ae05de63-b527-66e6-2c79-056c9c92ec95
description: "Locks an object from another program against being cropped with the Crop tool."
---

# LockCrop Cell (Protection Section)

Locks an object from another program against being cropped with the **Crop** tool. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Shape cannot be cropped  <br/> |
| FALSE  <br/> | Shape can be cropped. |
   
## Remarks

To get a reference to the LockCrop cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockCrop  <br/> |
   
To get a reference to the LockCrop cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLock** <br/> |
| **Cell index:**  <br/> |**visLockCrop** <br/> |
   

