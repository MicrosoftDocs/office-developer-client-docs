---
title: "LockThemeColors Cell (Protection Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm70001
 
ms.localizationpriority: medium
ms.assetid: 22cedeb3-58b5-3932-9252-5c9dd3e163e3

---

# LockThemeColors Cell (Protection Section)

Prevents application of theme colors to the shape. 
  
The value of the LockThemeColors cell corresponds to the **From theme colors** check box setting in the **Protection** dialog box. 
  
To refer to the LockThemeColors cell by name from another formula, or from a program, using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |LockThemeColors  <br/> |
   
To refer to the LockThemeColors cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowLock** <br/> |
|**Cell index:**  <br/> |**visLockThemeColors** <br/> |
   

