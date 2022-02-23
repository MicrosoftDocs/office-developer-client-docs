---
title: "BOUND Function" 
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60099 
ms.localizationpriority: medium
ms.assetid: 36374d78-1028-bd7f-6282-66555ee31306
description: "Constrains the value of a cell to a range or set of ranges."
---

# BOUND Function

Constrains the value of a cell to a range or set of ranges.
  
## Syntax

BOUND (***value***, ***type***, ***ignore***, ***value1***, ***value2*** ***[,ignore(n), value1(n), value2(n),...]*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *value* |Required |**Numeric** |The current value being constrained. |
| *type* |Required |**Numeric** |Whether the constraint is inclusive (0), exclusive (1), or disabled (2). |
| *ignore* |Required |**Boolean** | TRUE to ignore the range; FALSE to constrain the value of the cell to the range. |
| *value1* |Required |**Numeric** |First value in a range. |
| *value2* |Required |**Numeric** |Second value in a range. |

## Remarks

Use the BOUND function to restrict a cell's value to an upper and lower bound, for example, to control objects that should not be stretched above or below a minimum or maximum height. The constraint can be inclusive or exclusive with respect to the range or ranges. If the current value should not be constrained, set the *type* parameter to 2 (disabled).
  
You can define multiple ranges by supplying multiple occurrences of the *ignore*, *value1*, and *value2* parameters. Use the *ignore* parameter to disable constraints by a particular range.
  
The formula containing the BOUND function does not get overwritten when its value changes; instead, the formula is preserved and the new value is placed into the *value* parameter.
  
## Example 1

This example uses the BOUND function to force a control handle to stay within the bounding box of a shape.
  
Controls.X1 = BOUND(Width\*0.5, 0, FALSE, Width\*0, Width\*1)
  
Controls.Y1 = BOUND(Height\*0.5, 0, FALSE, Height\*0, Height\*1)
  
## Example 2

This example uses the BOUND function to constrain a shape's width to 2 inches, 4 inches, or 6 inches.
  
Width = BOUND(, 0, FALSE, 2 in, 2 in, FALSE, 4 in, 4 in, FALSE, 6 in, 6 in)
