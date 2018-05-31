---
title: "DAYOFYEAR Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251416
 
localization_priority: Normal
ms.assetid: 154d76a2-81f5-d8b1-b665-26dbae5da615
description: "Returns an integer, 1 to 366, that represents the sequential day of the year in datetime or expression. The DAYOFYEAR function uses the Gregorian calendar."
---

# DAYOFYEAR Function

Returns an integer, 1 to 366, that represents the sequential day of the year in  _datetime_ or  _expression_. The DAYOFYEAR function uses the Gregorian calendar.
  
## Syntax

DAYOFYEAR(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**String** <br/> |Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |Specifies the locale identifier to be used in evaluating a non-local datetime. The locale identifier is a number described in the system header files.  <br/> |
   
### Return value

Integer
  
## Remarks

Any time component in  _datetime_ or  _expression_ is discarded. 
  
The result corresponds to January 1 to December 31. No rounding is done. If  _datetime_ is missing or cannot be interpreted as a valid date or time, the function returns an error. 
  
The DAYOFYEAR function also accepts a single number value for  _expression_ where the integer portion of the result represents the number of days since December 30, 1899. 
  
## Example 1

DAYOFYEAR("May 30, 1997 13:45:24")
  
Returns 150.
  
## Example 2

DAYOFYEAR(DATEVALUE("May 30, 1997")+7 ed.)
  
Returns 157.
  
## Example 3

DAYOFYEAR(35580.6337)
  
Returns 150.
  

