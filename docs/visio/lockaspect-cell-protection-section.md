---
title: "LockAspect Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251218
 
ms.localizationpriority: medium
ms.assetid: e9bfced5-af29-f86c-8604-44ec9a573229
description: "Locks the aspect ratio of the shape so that the shape can only be sized proportionally; it cannot be sized in a single dimension."
---

# LockAspect Cell (Protection Section)

Locks the aspect ratio of the shape so that the shape can only be sized proportionally; it cannot be sized in a single dimension.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Aspect ratio is locked.  <br/> |
| FALSE  <br/> | Aspect ratio is not locked.  <br/> |
   
## Remarks

To get a reference to the LockAspect cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockAspect  <br/> |
   
To get a reference to the LockAspect cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockAspect** <br/> |
   

