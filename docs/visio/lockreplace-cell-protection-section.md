---
title: "LockReplace Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: b3880511-dd27-4dc2-9e50-a49084ef8195
description: "Indicates whether a shape can participate in a replacement operation (as either a target or a replacement shape)."
---

# LockReplace Cell (Protection Section)

Indicates whether a shape can participate in a replacement operation (as either a target or a replacement shape). 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The shape cannot be replaced or be used as a replacement shape. For a shape on the canvas, the **Change Shape** button is disabled when the shape is selected. For a shape on a stencil, the shape does not appear as a replacement shape when the **Change Shape** button is clicked. |
|FALSE  <br/> |The shape can be replaced or used as a replacement shape. |
   
## Remarks

To get a reference to the **LockReplace** cell by name from another formula, by value of the **N** attribute of a **Cell** element, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockReplace  <br/> |
   
To get a reference to the **LockReplace** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockReplace** <br/> |
   

