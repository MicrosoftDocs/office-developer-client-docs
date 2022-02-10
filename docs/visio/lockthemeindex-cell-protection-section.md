---
title: "LockThemeIndex Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 7b781727-267b-4589-ab40-cfc79bb96c2d
description: "Prevents ThemeIndex cell in Theme Properties row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet."
---

# LockThemeIndex Cell (Protection Section)

Prevents **ThemeIndex** cell in **Theme Properties** row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **ThemeIndex** cell cannot be changed from its current value unless changed in the ShapeSheet directly. |
|FALSE  <br/> |The **ThemeIndex** cell can be changed from its current value when the theme is changed. |
   
## Remarks

To get a reference to the **LockThemeIndex** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockThemeIndex  <br/> |
   
To get a reference to the **LockThemeIndex** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockThemeIndex** <br/> |
   

