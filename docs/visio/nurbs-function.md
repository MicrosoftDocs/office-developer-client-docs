---
title: "NURBS Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251579
 
ms.localizationpriority: medium
ms.assetid: f34db20d-6501-2026-a5e8-29c4d4cb2405
description: "Returns a nonuniform rational B-spline (NURBS). This function is used in the E cell in the NURBSTo geometry rows."
---

# NURBS Function

Returns a nonuniform rational B-spline (NURBS). This function is used in the E cell in the NURBSTo geometry rows.
  
## Syntax

NURBS(***knotLast***, ***degree***, ***xType***, ***yType***, ***x1***, ***y1***, ***knot1***, ***weight1***, ...)
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| *knotLast* <br/> |Required  <br/> |**string** <br/> | The last knot. |
| *degree* <br/> |Required  <br/> |**Numeric** <br/> |The spline's degree. |
| *xType* <br/> |Required  <br/> |**Numeric** <br/> |Specifies how to interpret the  *x* input data. If _xType_ is 0, all _x_ input data is interpreted as a percentage of Width. If _xType_ is 1, all _x_ input data is interpreted as local coordinates. |
| *yType* <br/> |Required  <br/> |**Numeric** <br/> |Specifies how to interpret the  *y* input data. If _yType_ is 0, all _y_ input data is interpreted as a percentage of Height. If _yType_ is 1, all _y_ input data is interpreted as local coordinates. |
| *x1* <br/> |Required  <br/> |**String** <br/> |An x-coordinate. |
| *y1* <br/> |Required  <br/> |**String** <br/> |A y-coordinate. |
| *knot1* <br/> |Required  <br/> |**String** <br/> |A knot on the B-spline. |
| *weight1* <br/> |Required  <br/> |**String** <br/> |A weight on the B-spline. |

## Remarks

For every  *x*  argument, there must be a  *y*  argument; otherwise, an error is returned.
  
You must specify at least one  *x*, *y*, *knot*, and  *weight*  argument; otherwise, Visio returns an error.
  