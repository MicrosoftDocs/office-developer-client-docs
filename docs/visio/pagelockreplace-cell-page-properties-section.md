---
title: "PageLockReplace Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 59c36555-42af-4729-aea7-0332d1da6e3b
description: "Indicates whether the Replace Shape button should be disabled for this page."
---

# PageLockReplace Cell (Page Properties Section)

Indicates whether the **Replace Shape** button should be disabled for this page. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **Change Shape** button is grayed out when this page is active.  <br/> |
|FALSE  <br/> |The **Change Shape** button is not disabled by this page. The button may still be grayed out if: the **DocLockReplace** on the **DocumentSheet** is set to **TRUE**; the **LockReplace** cell for the selected shape is set to **TRUE**.  <br/> |
   
## Remarks

To get a reference to the **PageLockReplace** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageLockReplace  <br/> |
   
To get a reference to the **PageLockReplace** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageLockReplace** <br/> |
   

