---
title: "INTERSECTX Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251444
 
localization_priority: Normal
ms.assetid: d8dc1915-f055-e858-1323-9e8c1cb7f2f1
description: "Returns the x -coordinate (in the local coordinate system) of the point where two lines intersect."
---

# INTERSECTX Function

Returns the  *x*  -coordinate (in the local coordinate system) of the point where two lines intersect. 
  
## Syntax

INTERSECTX( ** *x1* **, ** *y1* **, ** *angle1* **, ** *x2* **, ** *y2* **, ** *angle2* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _x1_ <br/> |Required  <br/> |**Number** <br/> |The  _x_-coordinate of a point on the first line.  <br/> |
| _y1_ <br/> |Required  <br/> |**Number** <br/> |The  _y_-coordinate of a point on the first line.  <br/> |
| _angle1_ <br/> |Required  <br/> |**Number** <br/> | The value of the Angle cell for the first line.  <br/> |
| _x2_ <br/> |Required  <br/> |**Number** <br/> |The  _x_-coordinate of a point on the second line.  <br/> |
| _y2_ <br/> |Required  <br/> |**Number** <br/> |The  _y_-coordinate of a point on the second line.  <br/> |
| _angle2_ <br/> |Required  <br/> |**Number** <br/> |The value of the Angle cell for the second line.  <br/> |
   
### Return value

Number
  
## Remarks

Each line is defined as a point (  *x,y*  ) and an angle. 
  
Microsoft Visio uses this function in the PinX cell of a shape glued to a rotated guide. 
  
If the lines don't intersect, the function returns a divide-by-zero error (#DIV/0!), which Visio ignores, restoring the last known value for the point. 
  
## Example

INTERSECTX(VertGuide!PinX,VertGuide!PinY,VertGuide!Angle, HorzGuide!PinX,HorzGuide!PinY,HorzGuide!Angle) 
  
Returns the  *x*  -coordinate of the intersection point of VertGuide and HorzGuide in page units. 
  

