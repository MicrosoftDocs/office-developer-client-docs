---
title: "DontMoveChildren Cell (Group Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm255
 
localization_priority: Normal
ms.assetid: ff5bbf05-4851-30ce-7ee1-f0ce7b2781ab
description: "Determines whether you can drag shapes in a group using the mouse."
---

# DontMoveChildren Cell (Group Properties Section)

Determines whether you can drag shapes in a group using the mouse.
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Don't allow shapes in a group to be dragged using the mouse.  <br/> |
| FALSE  <br/> | Allow shapes in a group to be dragged using the mouse.  <br/> |
   
## Remarks

When the value of this cell is TRUE, you can still flip, rotate, resize, or reposition shapes in groups using other methods.
  
The value of this cell is TRUE for groups in masters and groups in instances of masters that were created in versions of Visio earlier than version 2000.
  
To get a reference to the DontMoveChildren cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | DontMoveChildren  <br/> |
   
To get a reference to the DontMoveChildren cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowGroup** <br/> |
| Cell index:  <br/> |**visGroupDontMoveChildren** <br/> |
   

