---
title: "LockWidth Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm675
 
ms.localizationpriority: medium
ms.assetid: fef022ea-38ab-2b66-60c8-b94a6b0bdfbf
description: "Locks the width of the shape so that its width remains unchanged when the shape is sized."
---

# LockWidth Cell (Protection Section)

Locks the width of the shape so that its width remains unchanged when the shape is sized.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Width is locked. |
| FALSE  <br/> | Width is not locked. |
   
## Remarks

To get a reference to the LockWidth cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockWidth  <br/> |
   
To get a reference to the LockWidth cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLock** <br/> |
| **Cell index:**  <br/> |**visLockWidth** <br/> |
   

