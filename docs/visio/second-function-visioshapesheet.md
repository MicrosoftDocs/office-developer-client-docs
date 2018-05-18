---
title: "SECOND Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251495
 
localization_priority: Normal
ms.assetid: 22005976-37c0-d2be-8e34-8aee8458e4be
description: "Returns an integer, 0 to 59, that represents the seconds component of datetime or expression."
---

# SECOND Function (VisioShapeSheet)

Returns an integer, 0 to 59, that represents the seconds component of  _datetime_ or  _expression_.
  
## Syntax

SECOND(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**String** <br/> | Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Numeric** <br/> |The locale identifier to be used in evaluating a nonlocal  _datetime_. The locale identifier is a number described in the system header files.  <br/> |
   
### Return value

Integer
  
## Remarks

The date component in  _datetime_ or  _expression_ is discarded. 
  
No rounding is done. If  _datetime_ is missing or cannot be converted to a valid result, this function returns an error. 
  
The SECOND function also accepts a single number value for  _expression_ where the decimal portion of the result represents the fraction of a day since midnight. 
  
## Example 1

SECOND("05/30/1997 13:45:32")
  
Returns 32.
  
## Example 2

SECOND(TIMEVALUE("May 30, 1996 12:07:45") + 7 es.)
  
Returns 52.
  
## Example 3

SECOND(0.6337)
  
Returns 32.
  

