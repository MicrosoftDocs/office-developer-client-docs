---
title: "CEILING Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251405
 
localization_priority: Normal
ms.assetid: 1a8d6d48-7ae3-5483-28d2-5b1706088a53
description: "Rounds a number away from 0 (zero) to the next instance of multiple. If multiple is not specified, the number rounds away from 0 to the next integer."
---

# CEILING Function

Rounds a number away from 0 (zero) to the next instance of  _multiple_. If  _multiple_ is not specified, the number rounds away from 0 to the next integer. 
  
## Syntax

CEILING( ** *number* **, ** *multiple* ** ) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _number_ <br/> |Required  <br/> |**Number** <br/> |The number to round.  <br/> |
| _multiple_ <br/> |Required  <br/> |**Number** <br/> |The multiple to round to.  <br/> |
   
## Remarks

 _Number_ and  _multiple_ must have the same signs, or a #NUM! error is returned. If either  _number_ or  _multiple_ cannot be converted to a value, a #VALUE! error is returned. If either  _number_ or  _multiple_ is 0, the result is 0. 
  
## Example 1

CEILING(3.7)
  
Returns 4
  
## Example 2

CEILING(-3.7)
  
Returns -4
  
## Example 3

CEILING(3.7, 0.25)
  
Returns 3.75
  

