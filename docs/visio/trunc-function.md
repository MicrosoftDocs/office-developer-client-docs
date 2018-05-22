---
title: "TRUNC Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251508
 
localization_priority: Normal
ms.assetid: 62f074ef-5bf8-df1e-d826-fc1027a36501
description: "Returns a number truncated to the specified number of digits."
---

# TRUNC Function

Returns a number truncated to the specified number of digits.
  
## Syntax

TRUNC(** *number* **, ** *numberofdigits* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Numeric** <br/> |The number to truncate.  <br/> |
| _numberofdigits_ <br/> |Required  <br/> |**Numeric** <br/> |The number of digits to which to truncate  _number_.  <br/> |
   
### Return value

Numeric.
  
## Remarks

If  _numberofdigits_ is greater than 0,  _number_ is truncated to  _numberofdigits_ to the right of the decimal. If  _numberofdigits_ is 0,  _number_ is truncated to an integer. If  _numberofdigits_ is less than 0,  _number_ is truncated to  _numberofdigits_ to the left of the decimal. 
  
## Example 1

TRUNC(123.654,2)
  
Returns 123.65.
  
## Example 2

TRUNC(123.654,0)
  
Returns 123.
  
## Example 3

TRUNC(123.654,-1)
  
Returns 120.
  

