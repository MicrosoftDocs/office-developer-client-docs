---
title: "DAY Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251415
 
localization_priority: Normal
ms.assetid: 3b0842ae-6893-2d7b-6cb2-8905198fae30
description: "Returns an integer, 1 to 31, representing the day in datetime or expression. The DAY function uses the Gregorian calendar."
---

# DAY Function (VisioShapeSheet)

Returns an integer, 1 to 31, representing the day in  _datetime_ or  _expression_. The DAY function uses the Gregorian calendar.
  
## Syntax

DAY(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
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
  
No rounding is done. If  _datetime_ is missing or cannot be converted to a valid result, the function returns an error. 
  
The DAY function also accepts a single number value for  _expression_ where the integer portion of the result represents the number of days since December 30, 1899. 
  
## Example 1

DAY("May 30, 1997 15:45:24")
  
Returns 30.
  
## Example 2

DAY(DATEVALUE("May 30, 1997")+7 ed.)
  
Returns 6.
  
## Example 3

DAY(35580.6337)
  
Returns 30.
  

