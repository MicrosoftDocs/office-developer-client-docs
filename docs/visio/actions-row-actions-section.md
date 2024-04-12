---
title: "Actions Row (Actions Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60017
 
ms.localizationpriority: medium
ms.assetid: 29a7464a-b9d4-a8ea-161b-3044de32ed23
description: "Contains cells that specify the actions associated with a custom command on a shortcut or action tag menu. The Actions section contains one Actions row for each action."
---

# Actions Row (Actions Section)

Contains cells that specify the actions associated with a custom command on a shortcut or action tag menu. The Actions section contains one Actions row for each action.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags.
  
Actions rows are named Actions.*name* and contain the following cells. For more details, see the specific cell topics.
  
|**Cell**|**Description**|
|:-----|:-----|
|[Action](action-cell-actions-section.md) <br/> |Contains the formula to be executed when a user chooses an item on a shortcut or action tag menu. |
|[Menu](menu-cell-actions-section.md) <br/> |Defines the name of the menu item that appears on a action tag or shortcut menu. |
|[TagName](tagname-cell-actions-section.md) <br/> |The logical name of the action tag in which this action should appear. |
|[ButtonFace](buttonface-cell-actions-section.md) <br/> |Identifies the icon that appears next to an item on a shortcut or action tag menu. |
|[SortKey](sortkey-cell-actions-section.md) <br/> |A number that determines the order of menu items on a action tag or shortcut menu. |
|[Checked](checked-cell-actions-section.md) <br/> |Indicates whether the menu item is checked on a action tag or shortcut menu. |
|[Disabled](disabled-cell-actions-section.md) <br/> |Indicates whether a menu item on a shortcut or action tag menu is disabled. |
|[ReadOnly](readonly-cell-actions-section.md) <br/> |Indicates whether the menu item is read-only (cannot be clicked). |
|[Invisible](invisible-cell-actions-section.md) <br/> |Indicates whether the menu item is visible on the action tag or shortcut menu. |
|[BeginGroup](begingroup-cell-actions-section.md) <br/> |Indicates whether to insert a separator into the menu, above the menu item. |

## Remarks

 You can add as many Actions. *name* rows as you need, assign meaningful names to the rows, and set cell values. To add a custom command to an existing Actions section, right-click a row and click **Insert Row** on the shortcut menu.
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign a meaningful name to an Actions. *name* row, click the row, and then type a name such as *Custom*, for example, to create the row name Actions.Custom. You can then reference the Menu cell by using Actions.Custom.Menu.
  
The row name you enter must be unique within the section.
  