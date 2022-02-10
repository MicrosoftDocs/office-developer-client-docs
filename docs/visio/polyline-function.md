---
title: "POLYLINE Function"
 
 
manager: soliver
ms.date: 03/09/2015
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

POLYLINE(** *xType* **, ** *yType* **, ** *x1* **, ** *y1* **...) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _xType_ <br/> |Required  <br/> |**Boolean** <br/> |Specifies how to interpret the  _x_ input data. If  _xType_ is 0, the input  _x_-data is interpreted as a percentage of Width. If  _xType_ is 1, the input  _x_-data is interpreted as a local coordinate. |
| _yType_ <br/> |Required  <br/> |**Boolean** <br/> |Specifies how to interpret the  _y_-input data. If  _yType_ is 0, the input  _y_-data is interpreted as a percentage of Height. If  _yType_ is 1, the input  _y_-data is interpreted as a local coordinate. |
| _x1_ <br/> |Required  <br/> |**Number** <br/> | An  _x_-coordinate. |
| _y1_ <br/> |Required  <br/> |**Number** <br/> |A  _y_-coordinate. |
   
## Remarks

For every  *x*  argument, there must be a  *y*  argument; otherwise, an error is returned. 
  
## Example

POLYLINE (0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0) 
  
Returns a rectangle of dimensions Width x Height. 
  

