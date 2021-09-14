---
title: "LockFormat Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm625
 
ms.localizationpriority: medium
ms.assetid: e9a640f4-0af0-317c-b77b-f32c651e87b4
description: "Locks the formatting of a shape so it cannot be changed."
---

# LockFormat Cell (Protection Section)

Locks the formatting of a shape so it cannot be changed.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Formatting cannot be changed.  <br/> |
| FALSE  <br/> | Formatting can be changed.  <br/> |
   
## Remarks

To get a reference to the LockFormat cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockFormat  <br/> |
   
To get a reference to the LockFormat cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockFormat** <br/> |
   

