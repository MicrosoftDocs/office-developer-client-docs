---
title: "PAR Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251477
 
localization_priority: Normal
ms.assetid: 9caf424d-cb70-8f1a-b984-64cf776bdfb4
description: "Returns the x,y coordinates of a point in the coordinate system of the shape's parent."
---

# PAR Function

Returns the  _x,y_ coordinates of a point in the coordinate system of the shape's parent. 
  
## Syntax

PAR( ** *point* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _point_ <br/> |Required  <br/> |**Number, Number** <br/> |The coordinates of the point in the coordinate system of the current shape.  <br/> |
   
## Remarks

In Microsoft Visio, a point is a single value that embodies a pair of  *x*  - and  *y*  -coordinates. If the shape is in a group, its parent is the group. If the shape is not in a group, its parent is the page. 
  
## Example

PAR(PNT(PinX,PinY)) 
  
In this expression, PNT converts a pair of coordinates in the current shape into a point. PAR then converts the point into a pair of coordinates in relation to the lower-left corner of the page or group that contains the current shape. 
  

