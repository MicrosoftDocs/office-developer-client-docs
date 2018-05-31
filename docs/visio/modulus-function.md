---
title: "MODULUS Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251465
 
localization_priority: Normal
ms.assetid: cb6326a5-1bf8-b6a3-5c0d-d38c071353a5
description: "Returns the remainder (modulus) that results when a number is divided by a divisor."
---

# MODULUS Function

Returns the remainder (modulus) that results when a number is divided by a divisor.
  
## Syntax

MODULUS(** *number* **, ** *divisor* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Number** <br/> |The dividend.  <br/> |
| _divisor_ <br/> |Required  <br/> |**Number** <br/> |The divisor.  <br/> |
   
### Return value

Number
  
## Remarks

The result has the same sign as the divisor. A #DIV/0! error is returned if the divisor is 0. 
  
In almost all situations, the MODULUS function should be used rather than the MOD function. 
  
## Example 1

MODULUS(5, 1.4)
  
Returns 0.8.
  
## Example 2

MODULUS(5, -1.4)
  
Returns -0.6.
  
## Example 3

MODULUS(-5, 1.4)
  
Returns 0.6.
  
## Example 4

MODULUS(-5, -1.4)
  
Returns -0.8.
  

