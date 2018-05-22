---
title: "SIGN Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251497
 
localization_priority: Normal
ms.assetid: fdc032c2-d0bd-1592-de3f-33c478d066ee
description: "Returns a value that represents the sign of a number."
---

# SIGN Function

Returns a value that represents the sign of a number. 
  
## Syntax

SIGN(** *number* **, ** *fuzz* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Numeric** <br/> | The number for which you want to determine the sign.  <br/> |
| _fuzz_ <br/> |Optional  <br/> |**Numeric** <br/> |Specifies how close to zero the number must be in order to be considered equal to zero.  <br/> |
   
### Return value

Numeric
  
## Remarks

The SIGN function returns 1 if  _number_ is positive, 0 if  _number_ is zero, or -1 if  _number_ is negative. 
  
Specifyin a  _fuzz_ value helps avoid floating-point roundoff errors when a calculation is almost zero. If you do not specify a  _fuzz_ value, Visio uses 1E-9 (0.000000001). You may want to supply a different value when you scale drawings or when you want an exact comparison. 
  
## Example 1

SIGN(-5)
  
Returns -1.
  
## Example 2

SIGN(0)
  
Returns 0.
  
## Example 3

SIGN(0.00000000001)
  
Returns 0.
  
## Example 4

SIGN(0.00000000001,0)
  
Returns 1.
  

