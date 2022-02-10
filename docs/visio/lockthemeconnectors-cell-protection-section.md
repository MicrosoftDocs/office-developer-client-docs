---
title: "LockThemeConnectors Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: ae7ddd55-7bcc-4bb6-bab7-97806122f166
description: "Prevents the ConnectorsSchemeIndex cell in the Theme Properties row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet."
---

# LockThemeConnectors Cell (Protection Section)

Prevents the **ConnectorsSchemeIndex** cell in the **Theme Properties** row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **ConnectorsSchemeIndex** cell cannot be changed from its current value unless changed in the ShapeSheet directly. |
|FALSE  <br/> |The **ConnectorsSchemeIndex** cell can be changed from its current value through the UI. |
   
## Remarks

To get a reference to the **LockThemeConnectors** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockThemeConnectors  <br/> |
   
To get a reference to the **LockThemeConnectors** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockThemeConnectors** <br/> |
   

