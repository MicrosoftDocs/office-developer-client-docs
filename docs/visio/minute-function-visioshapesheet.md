---
title: "MINUTE Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251464
 
localization_priority: Normal
ms.assetid: 5a90cb16-7eef-8876-8e25-408787b16f58
description: "Returns an integer from 0 to 59 that represents the minutes component of datetime or expression ."
---

# MINUTE Function (VisioShapeSheet)

Returns an integer from 0 to 59 that represents the minutes component of  *datetime*  or  *expression*  . 
  
## Syntax

MINUTE(" *datetime*  "|  *expression*  [,  *lcid*  ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**String** <br/> | Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |The locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files.  <br/> |
   
### Return value

Integer
  
## Remarks

The date component in  _datetime_ and  _expression_ is discarded. 
  
No rounding is done. If  _datetime_ is missing or cannot be converted to a valid result, the function returns an error. 
  
The returned value is formatted according to the time style set by the system's current Regional Settings.
  
The MINUTE function also accepts a single number value for  _expression_ where the decimal portion represents the fraction of a day since midnight. 
  
## Example 1

MINUTE("7/7/1999 13:45:24")
  
Returns 45.
  
## Example 2

MINUTE(TIMEVALUE("Jan. 25, 1999 12:07:45")+6 em.)
  
Returns 13.
  
## Example 3

MINUTE(0.575)
  
Returns 48.
  

