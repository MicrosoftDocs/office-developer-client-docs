---
title: "LockVtxEdit Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251224
 
ms.localizationpriority: medium
ms.assetid: 966cde5c-f04e-7149-3660-720ffa4f7079
description: "Locks the vertices of a shape so that they cannot be edited."
---

# LockVtxEdit Cell (Protection Section)

Locks the vertices of a shape so that they cannot be edited.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Vertices cannot be edited. |
|FALSE  <br/> |Vertices can be edited. |
   
## Remarks

To get a reference to the LockVtxEdit cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LockVtxEdit  <br/> |
   
To get a reference to the LockVtxEdit cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowLock** <br/> |
|**Cell index:**  <br/> |**visLockVtxEdit** <br/> |
   

