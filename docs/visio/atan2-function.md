---
title: "ATAN2 Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251397
 
localization_priority: Normal
ms.assetid: 524278fb-196e-9cf9-e27b-d03642beeee4
description: "Returns the angle between the vector represented by x,y and the direction of the x -axis. The result is a number in the current unit of measure for angles."
---

# ATAN2 Function

Returns the angle between the vector represented by  *x,y*  and the direction of the  *x*  -axis. The result is a number in the current unit of measure for angles. 
  
## Syntax

ATAN2( ** *y* **, ** *x* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _y_ <br/> |Required  <br/> |**Numeric** <br/> |The  _y_-value of the point.  <br/> |
| _x_ <br/> |Required  <br/> |**Numeric** <br/> |The  _x_-value of the point.  <br/> |
   
## Remarks

The arctangent is the angle measured counterclockwise from the positive  *x*  -axis to a line that intersects the origin (0,0) and the point represented by  *x*  and  *y*  . In Microsoft Visio, ATAN2(0,0) returns 0. To force the result of ATAN2 into a different angular measurement, use the DEG or RAD function. 
  
The ATAN2 function is the antifunction of the TAN function. The ATAN2 function returns the angle whose angle is equal to  *y*  divided by  *x*  . If ATAN2(  *y,x*  ) represents an angle in a right triangle,  *y*  is the "opposite side" and  *x*  is the "adjacent side," so the function could be written as ATAN2(opposite,adjacent). 
  
## Example 1

ATAN2(1.25,2.25)
  
Returns 29.0456 deg
  
## Example 2

ATAN2(1,SQRT(3))
  
Returns 30 deg
  
## Example 3

ATAN2(1,1)
  
Returns 45 deg
  

