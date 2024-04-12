---
title: "ReadOnly Cell (Actions Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60071
 
ms.localizationpriority: medium
ms.assetid: 158b4188-570c-3817-bf34-8dc0c64befa5
description: "Controls whether the action on an action tag or shortcut menu is read-only."
---

# ReadOnly Cell (Actions Section)

Controls whether the action on an action tag or shortcut menu is read-only. 
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The action appears on the menu but is read-only. |
|FALSE  <br/> |The action appears on the menu and can be selected (the default). |
   
## Remarks

When an action is read-only, it appears on the action tag or shortcut menu but you cannot select it. It is not dimmed but rather appears on a colored background, like a label. To make the menu item appear dimmed, use the Disabled cell. 
  
To get a reference to the ReadOnly cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Actions. *name*  .ReadOnlywhere Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the ReadOnly cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionAction** <br/> |
|**Row index:**  <br/> |**visRowAction** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visActionReadOnly** <br/> |
   

