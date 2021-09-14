---
title: "LockRotate Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm655
 
ms.localizationpriority: medium
ms.assetid: 2d97b31d-9008-307d-273a-1726007eeb34
description: "Locks 2-D shapes against being rotated with the rotation handle or the Rotate Left 90° or Rotate Right 90° command."
---

# LockRotate Cell (Protection Section)

Locks 2-D shapes against being rotated with the rotation handle or the **Rotate Left 90°** or **Rotate Right 90°** command. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Shape cannot be rotated.  <br/> |
| FALSE  <br/> | Shape can be rotated (the default).  <br/> |
   
## Remarks

The LockRotate cell does not prevent a 1-D shape from being rotated when an endpoint is dragged. To lock a 1-D shape against rotation, set the LockWidth cell to a non-zero value (TRUE).
  
To get a reference to the LockRotate cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockRotate  <br/> |
   
To get a reference to the LockRotate cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockRotate** <br/> |
   

