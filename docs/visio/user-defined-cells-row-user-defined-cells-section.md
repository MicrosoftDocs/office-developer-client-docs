---
title: "User-defined Cells Row (User-defined Cells Section)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm3060
 
ms.localizationpriority: medium
ms.assetid: 6c48b9b3-5c62-7d5a-1c8f-fe96606f4dea
description: "Contains the value and descriptive prompt for any user-defined cells in your solution. A shape contains one User-defined Cells row for each user-defined Value/Prompt cell pair."
---

# User-defined Cells Row (User-defined Cells Section)

Contains the value and descriptive prompt for any user-defined cells in your solution. A shape contains one User-defined Cells row for each user-defined Value/Prompt cell pair.
  
User-defined Cells rows are named User. *name*  and contain the following cells. For more details, see the specific cell topics.
  
|**Cell**|**Description**|
|:-----|:-----|
|[Value](value-cell-user-defined-cells-section.md) <br/> |Specifies a value for the corresponding user-defined cell. |
|[Prompt](prompt-cell-user-defined-cells-section.md) <br/> |Specifies a descriptive prompt or comment for the user-defined cell. |

## Remarks

User-defined cells can be used for entering formulas or constants that are referred to by other cells or add-ons. Values in user-defined cells are portable, that is, if a shape that refers to a user-defined cell in one shape is copied to another shape that does not have the same user-defined cell, the cell is added to the shape.
  
 You can add as many User.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add a row to an existing User-defined Cells section, right-click a row and click **Insert Row** on the shortcut menu.
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign meaningful names to User. *name*  rows, click the row, and then type a name such as *Offset*, for example, to create the row name User.Offset. You can then reference the Prompt cell using User.Offset.Prompt.
  
The row name you enter must be unique within the section.
  