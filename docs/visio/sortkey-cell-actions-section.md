---
title: "SortKey Cell (Actions Section)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1027286
 ms.localizationpriority: medium
ms.assetid: c0c4b668-f31b-336f-4434-e94a4804ff7c
description: "A number that determines the order of actions that appear on a shortcut or action tag menu."
---

# SortKey Cell (Actions Section)

A number that determines the order of actions that appear on a shortcut or action tag menu.
  
> [!NOTE]
> In previous versions of Microsoft Visio, action tags are called smart tags.
  
## Remarks

The actions on an action tag or shortcut menu appear on the menu sorted from lowest to highest, with lower numbers appearing at the top of the menu. If two action rows have the same SortKey cell value, the order is determined by physical row order. The default is 0 (zero).
  
To get a reference to the SortKey cell by name from another formula, or from a program by using the **CellsU** property, use:
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions. *name* .SortKeywhere Actions. *name* is the name of the Actions row  <br/> |

To get a reference to the SortKey cell by index from a program, use the **CellsSRC** property with the following arguments:
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*  where  *i*  = 0, 1, 2... |
|Cell index:  <br/> |**visActionSortKey** <br/> |
