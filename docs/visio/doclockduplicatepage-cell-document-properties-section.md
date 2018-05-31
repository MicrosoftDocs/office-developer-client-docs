---
title: "DocLockDuplicatePage Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: b08a6558-519f-44e0-aeff-9919544d515e
description: "Determines whether pages in the document can be duplicated, as a Boolean."
---

# DocLockDuplicatePage Cell (Document Properties Section)

Determines whether pages in the document can be duplicated, as a Boolean.
  
|||
|:-----|:-----|
|TRUE  <br/> |**Duplicate** in the page shortcut menu and the **Page.Duplicate** automation method are both disabled.  <br/> |
|FALSE  <br/> |The page can be duplicated.  <br/> |
   
## Remarks

To get a reference to the **DocLockDuplicatePage** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | DocLockDuplicatePage  <br/> |
   
To get a reference to the **DocLockDuplicatePage** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowDoc** <br/> |
| Cell index:  <br/> |**visDocLockDuplicatePage** <br/> |
   

