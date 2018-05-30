---
title: "PageLockDuplicate Cell (Page Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: fbaa7d64-06ef-46d6-81d5-9d7af1c14b65
description: "Determines whether the page can be duplicated, as a Boolean."
---

# PageLockDuplicate Cell (Page Properties Section)

Determines whether the page can be duplicated, as a Boolean.
  
|||
|:-----|:-----|
|TRUE  <br/> |**Duplicate** in the page shortcut menu and the **Page.Duplicate** automation method are both disabled for the page.  <br/> |
|FALSE  <br/> |The page can be duplicated.  <br/> |
   
## Remarks

To get a reference to the **PageLockDuplicate** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | PageLockDuplicate  <br/> |
   
To get a reference to the **PageLockDuplicate** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowPage** <br/> |
| Cell index:  <br/> |**visPageLockDuplicate** <br/> |
   

