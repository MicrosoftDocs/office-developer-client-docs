---
title: "GREEN Function" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251434
 
ms.localizationpriority: medium
ms.assetid: eccec432-32d3-15c2-06b3-dd02b6313d4c
description: "Returns the green component of a color."
---

# GREEN Function

Returns the green component of a color.
  
## Syntax

GREEN(***expression*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *expression* <br/> |Required  <br/> |**Varies** <br/> |An index of a color in the document's color table, an expression that resolves to a custom color (such as RGB or HSL), or a reference to a cell that contains a color index or color result. |

### Return value

Integer
  
## Remarks

The return value is a number in the range 0 to 255, inclusive, or a cell reference that resolves to an index. If  *expression*  is invalid, it returns 0 (black).
  
## Example 1

GREEN(Sheet.4!FillForegnd)
  
Returns the green component of Sheet.4's fill foreground color.
  
## Example 2

GREEN(11)
  
Returns 128 if the document uses the default Visio color palette, where dark yellow is the color at index 11.
  
## Example 3

GREEN(RGB(10, 20, 30))
  
Returns 20.
  