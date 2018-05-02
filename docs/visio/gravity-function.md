---
title: "GRAVITY Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251433
 
localization_priority: Normal
ms.assetid: db80f147-71a0-0b23-bc7e-fe1915dfdd21
description: "Calculates a text block's correct angle of rotation for the indicated shape rotation to prevent the text from turning upside down."
---

# GRAVITY Function

Calculates a text block's correct angle of rotation for the indicated shape rotation to prevent the text from turning upside down.
  
## Syntax

GRAVITY( ** *angle* **,[ ** *limit1* ** ],[ ** *limit2* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _angle_ <br/> |Required  <br/> |**String** <br/> | The shape's angle.  <br/> |
| _limit1_ <br/> |Optional  <br/> |**String** <br/> |First limit of rotation. Default is 90 degrees.  <br/> |
| _limit2_ <br/> |Optional  <br/> |**String** <br/> |Second limit of rotation. Default is 270 degrees.  <br/> |
   
### Return Value

String
  
## Remarks

The GRAVITY function is usually used in the TxtAngle cell. 
  
The value returned is 180 degrees if  _angle_ is between the values specified by  _limit1_ and  _limit2_; otherwise the value returned is 0 degrees.
  
All of the arguments are automatically normalized between 0 and 360 degrees by the function. If an argument does not specify units, radians are assumed. 
  
## Example 1

GRAVITY(Angle)
  
Returns 180 degrees if  *angle*  is between 90 and 270 degrees; otherwise, returns 0 degrees. 
  
## Example 2

GRAVITY(2)
  
Returns 180 degrees, because 2 radians is between 90 and 270 degrees.
  
## Example 3

GRAVITY(100 deg, 110 deg, 290 deg)
  
Returns 0 degrees.
  
## Example 4

GRAVITY(100 deg, 290 deg, 110 deg)
  
Returns 0 degrees.
  

