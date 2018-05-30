---
title: "POW Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251483
 
localization_priority: Normal
ms.assetid: c6519c55-5f98-ed0d-95b1-5443d0d23c0b
description: "Returns a number raised to the power of an exponent."
---

# POW Function

Returns a number raised to the power of an exponent.
  
## Syntax

POW(** *number* **, ** *exponent* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Number** <br/> |The number to raise to the power of an exponent.  <br/> |
| _exponent_ <br/> |Required  <br/> |**Number** <br/> |The exponent.  <br/> |
   
## Remarks

Both  _number_ and  _exponent_ may be non-integers, and they may be negative. If  _number_ is not 0 and  _exponent_ is 0, this function returns 1. If  _number_ is 0 and  _exponent_ is negative, this function returns 0.0. If both  _number_ and  _exponent_ are 0, or if  _number_ is negative and  _exponent_ is not an integer, this function returns 0.0. If both  _number_ and  _exponent_ are negative, this function returns -1.#IND. 
  
## Example

POW(5,2) 
  
Returns 25. 
  

