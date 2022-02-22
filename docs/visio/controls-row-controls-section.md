---
title: "Controls Row (Controls Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1024624
 
ms.localizationpriority: medium
ms.assetid: a57bdcd9-566b-5054-7458-7d84cbb78d23
description: "Contains cells that define the x - and y -coordinates and behavior of each control handle defined for a shape. A shape will contain one Controls row for each control handle."
---

# Controls Row (Controls Section)

Contains cells that define the  *x*  - and  *y*  -coordinates and behavior of each control handle defined for a shape. A shape will contain one Controls row for each control handle.
  
Controls rows are named Controls. *name*  and contain the following cells. For more details, see the specific cell topics.
  
|**Cell**|**Description**|
|:-----|:-----|
|[x](x-cell-controls-section.md) <br/> |Represents the *x* - coordinate that indicates the location of a shape's control handle in local coordinates. |
|[y](y-cell-controls-section.md) <br/> |Represents the *y* - coordinate that indicates the location of a shape's control handle in local coordinates. |
|[X Dynamics](x-dynamics-cell-controls-section.md) <br/> |Represents the *x* - coordinate for a control handle's anchor point in local coordinates. |
|[Y Dynamics](y-dynamics-cell-controls-section.md) <br/> |Represents the *y* - coordinate for a control handle's anchor point in local coordinates. |
|[X Behavior](x-behavior-cell-controls-section.md) <br/> |Controls the type of behavior the *x* - coordinate of the control handle will exhibit after the handle is moved. |
|[Y Behavior](y-behavior-cell-controls-section.md) <br/> |Controls the type of behavior the *y* - coordinate of the control handle will exhibit after the handle is moved. |
|[Can Glue](can-glue-cell-controls-section.md) <br/> |Determines whether a control handle can be glued to other shapes. |
|[Tip](tip-cell-controls-section.md) <br/> |Represents a descriptive text string that appears as a ToolTip when a user pauses the pointer over a shape's control handle. |

## Remarks

 You can add as many Controls.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add control handles to an existing Controls section, right-click a row and click **Insert Row** on the shortcut menu.
  
You can reference these cells by their row name, which appears in a ShapeSheet window in red text. To assign meaningful names to Controls. *name* rows, click the row and then type *Custom*, for example, to create the row name Controls.Custom. You can then reference the X cell using Controls.Custom.X.
  
The row name you enter must be unique within the section.
  