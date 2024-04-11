---
title: "FLOOR Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251423
 
ms.localizationpriority: medium
ms.assetid: 6788bc96-cc86-5f21-781f-67274e7f605a
description: "Rounds a number toward 0 (zero), to the next integer, or to the next instance of multiple."
---

# FLOOR Function

Rounds a number toward 0 (zero), to the next integer, or to the next instance of _multiple_.
  
## Syntax

FLOOR(***number***, ***multiple*** )
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Number** <br/> |The number to round. |
| _multiple_ <br/> |Required  <br/> |**Number** <br/> |The multiple to which to round. |

### Return value

Number
  
## Remarks

If _multiple_ is not specified, the number rounds toward 0 to the next integer.
  
 _Number_ and _multiple_ must have the same signs, or a #NUM! error is returned. If either _number_ or _multiple_ cannot be converted to a value, a #VALUE! error is returned. If either _number_ or _multiple_ is 0, the result is 0.
  
## Example 1

FLOOR(3.7)
  
Returns 3.
  
## Example 2

FLOOR(-3.7)
  
Returns -3.
  
## Example 3

FLOOR(3.7, 0.5)
  
Returns 3.5.
  