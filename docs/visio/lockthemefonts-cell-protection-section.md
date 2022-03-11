---
title: "LockThemeFonts Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 1ce8b52c-b6c1-4764-b4ec-00c7efb8929d
description: "Prevents the FontIndex cell in the Theme Properties row from being altered by applying a new theme. Does not prevent users from manually editing this value in the ShapeSheet."
---

# LockThemeFonts Cell (Protection Section)

Prevents the **FontIndex** cell in the **Theme Properties** row from being altered by applying a new theme. Does not prevent users from manually editing this value in the ShapeSheet. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **FontIndex** cell cannot be changed from its current value unless changed in the ShapeSheet directly. |
|FALSE  <br/> |The **FontIndex** cell can be changed from its current value when the theme is changed. |
   
## Remarks

To get a reference to the **LockThemeFonts** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | LockThemeFonts  <br/> |
   
To get a reference to the **LockThemeFonts** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionObject** <br/> |
| **Row index:**  <br/> |**visRowLock** <br/> |
| **Cell index:**  <br/> |**visLockThemeFonts** <br/> |
   

