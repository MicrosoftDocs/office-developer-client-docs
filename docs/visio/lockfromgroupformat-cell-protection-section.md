---
title: "LockFromGroupFormat Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: abd175af-ad4e-b84a-2687-2c9358653499

---

# LockFromGroupFormat Cell (Protection Section)

Blocks format changes to a group shape from being propagated to its sub-shapes, while still allowing users to format selected sub-shapes directly. 
  
The value of the LockFromGroupFormat cell corresponds to the **From group formatting** check box setting in the **Protection** dialog box. 
  
To refer to the LockFromGroupFormat cell by name from another formula, or from a program, using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LockFromGroupFormat  <br/> |
   
To refer to the LockFromGroupFormat cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowLock** <br/> |
|**Cell index:**  <br/> |**visLockFromGroupFormat** <br/> |
   
The default value for the cell is 0 (False).
  

