---
title: "POLYLINE Function" 
manager: lindalu
ms.date: 03/09/2022
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251576
 
ms.localizationpriority: medium
ms.assetid: 10baeec9-6c9b-b4ba-3138-7d1156a9e056
description: "Returns a polyline. This function is used in the A cell of PolyLineTo geometry rows."
---

# POLYLINE Function

Returns a polyline. This function is used in the A cell of PolyLineTo geometry rows.
  
## Syntax

POLYLINE(***xType***, ***yType***, ***x1***, ***y1***...)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *xType* <br/> |Required  <br/> |**Boolean** <br/> |Specifies how to interpret the *x* input data. If *xType* is 0, the input *x*-data is interpreted as a percentage of Width. If *xType* is 1, the input *x*-data is interpreted as a local coordinate. |
| *yType* <br/> |Required  <br/> |**Boolean** <br/> |Specifies how to interpret the *y*-input data. If *yType* is 0, the input *y*-data is interpreted as a percentage of Height. If *yType* is 1, the input *y*-data is interpreted as a local coordinate. |
| *x1* <br/> |Required  <br/> |**Number** <br/> | An *x*-coordinate. |
| *y1* <br/> |Required  <br/> |**Number** <br/> |A *y*-coordinate. |

## Remarks

For every  *x* argument, there must be a  *y* argument; otherwise, an error is returned.
  
## Example

POLYLINE (0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0)
  
Returns a rectangle of dimensions Width x Height.
  