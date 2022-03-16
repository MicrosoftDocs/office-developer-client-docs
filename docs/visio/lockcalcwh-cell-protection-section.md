---
title: "LockCalcWH Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm605
 
ms.localizationpriority: medium
ms.assetid: 6eb51e5a-03d8-3daa-b4e1-6107d540aed9
description: "Locks a shape's selection rectangle so it cannot be recalculated when a vertex is edited or a row type is changed in the Geometry section."
---

# LockCalcWH Cell (Protection Section)

Locks a shape's selection rectangle so it cannot be recalculated when a vertex is edited or a row type is changed in the Geometry section.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Width and height cannot be recalculated. |
| FALSE  <br/> | Width and height can be recalculated. |
   
## Remarks

To get a reference to the LockCalcWH cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockCalcWH  <br/> |
   
To get a reference to the LockCalcWH cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLock** <br/> |
| **Cell index:**  <br/> |**visLockCalcWH** <br/> |
   

