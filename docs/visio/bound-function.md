---
title: "BOUND Function"
 
 
manager: soliver
ms.date: 03/09/2015
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

BOUND (** *value* **, ** *type* **, ** *ignore* **, ** *value1* **, ** *value2* ** ** * [,ignore(n), value1(n), value2(n),...] * ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _value_ <br/> |Required  <br/> |**Numeric** <br/> |The current value being constrained. |
| _type_ <br/> |Required  <br/> |**Numeric** <br/> |Whether the constraint is inclusive (0), exclusive (1), or disabled (2). |
| _ignore_ <br/> |Required  <br/> |**Boolean** <br/> | TRUE to ignore the range; FALSE to constrain the value of the cell to the range. |
| _value1_ <br/> |Required  <br/> |**Numeric** <br/> |First value in a range. |
| _value2_ <br/> |Required  <br/> |**Numeric** <br/> |Second value in a range. |
   
## Remarks

Use the BOUND function to restrict a cell's value to an upper and lower bound, for example, to control objects that should not be stretched above or below a minimum or maximum height. The constraint can be inclusive or exclusive with respect to the range or ranges. If the current value should not be constrained, set the  _type_ parameter to 2 (disabled). 
  
You can define multiple ranges by supplying multiple occurrences of the  _ignore_,  _value1_, and  _value2_ parameters. Use the  _ignore_ parameter to disable constraints by a particular range. 
  
The formula containing the BOUND function does not get overwritten when its value changes; instead, the formula is preserved and the new value is placed into the  _value_ parameter. 
  
## Example 1

This example uses the BOUND function to force a control handle to stay within the bounding box of a shape. 
  
Controls.X1 = BOUND(Width\*0.5, 0, FALSE, Width\*0, Width\*1)
  
Controls.Y1 = BOUND(Height\*0.5, 0, FALSE, Height\*0, Height\*1)
  
## Example 2

This example uses the BOUND function to constrain a shape's width to 2 inches, 4 inches, or 6 inches. 
  
Width = BOUND(, 0, FALSE, 2 in, 2 in, FALSE, 4 in, 4 in, FALSE, 6 in, 6 in)
  

