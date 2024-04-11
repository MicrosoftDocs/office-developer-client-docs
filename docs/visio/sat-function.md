---
title: "SAT Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251494
 
ms.localizationpriority: medium
ms.assetid: 407817fb-9e4a-d2ca-6125-2440d2a417c6
description: "Returns the value of a color's saturation component."
---

# SAT Function

Returns the value of a color's saturation component.
  
## Syntax

SAT(***expression*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *expression* <br/> |Required  <br/> |**Varies** <br/> |An index of a color in the document's color table, an expression that resolves to a custom color (like RGB or HSL), or a reference to a cell that contains a color index or color result. |

### Return value

Numeric
  
## Remarks

The return value is a number in the range 0 to 240, inclusive. The function returns 0 for invalid input.
  
## Example 1

SAT(Sheet.4!FillForegnd)
  
Returns the saturation of Sheet.4's fill foreground color.
  
## Example 2

SAT(8)
  
Returns 240 if the document uses the default Visio color palette, where dark red is the color at index 8.
  
## Example 3

SAT(HSL(10, 20, 30))
  
Returns 20.
  