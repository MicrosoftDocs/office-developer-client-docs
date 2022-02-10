---
title: "LockVariation Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 36acb95d-5d3b-4d8b-9b6c-effbc78c84c2
description: "Determines whether the theme variation applied to the page or shape can be changed, as a Boolean."
---

# LockVariation Cell (Protection Section)

Determines whether the theme variation applied to the page or shape can be changed, as a Boolean.
  
|||
|:-----|:-----|
|TRUE  <br/> |The current variation applied to the page or shape cannot be changed. |
|FALSE  <br/> |The variation of the page or shape can be changed. |
   
## Remarks

To get a reference to the **LockVariation** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockVariation  <br/> |
   
To get a reference to the **LockVariation** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockVariation** <br/> |
   

