---
title: "LockSelect Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm660
 
ms.localizationpriority: medium
ms.assetid: c96b45a5-719e-8c4b-71b9-cb2224d83e21
description: "Prevents a shape from being selected."
---

# LockSelect Cell (Protection Section)

Prevents a shape from being selected.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Shape cannot be selected. |
| FALSE  <br/> | Shape can be selected. |
   
## Remarks

In order for LockSelect to take effect, the **Shapes** check box must be selected in the **Protect Document** dialog box. 
  
To get a reference to the LockSelect cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockSelect  <br/> |
   
To get a reference to the LockSelect cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockSelect** <br/> |
   

