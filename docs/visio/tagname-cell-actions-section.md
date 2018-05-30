---
title: "TagName Cell (Actions Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60087
 
localization_priority: Normal
ms.assetid: e593e95d-f975-481d-69cd-619049d4427d
description: "Contains the name of the action tag that this action is associated with."
---

# TagName Cell (Actions Section)

Contains the name of the action tag that this action is associated with.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
## Remarks

The TagName cell in the Actions section works together with the TagName cell in the Action Tags section to associate an action tag with its actions. 
  
- If the TagName cell in an Actions row is blank, the action appears on a shortcut menu, not on an action tag menu.
    
- If a TagName cell value in the Actions row matches the TagName cell value in a Smart Tags row, the action appears on the action tag menu.
    
- If an action's TagName cell has a value but it does not match the TagName value in any shape tag row, that action does not appear on any action tag menus or shortcut menus.
    
- If several smart tag rows have the same TagName value, they will all show the same actions.
    
To get a reference to the TagName cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions. *name*  .TagNamewhere Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the TagName cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visActionTagName** <br/> |
   

