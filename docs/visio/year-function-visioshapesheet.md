---
title: "YEAR Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251513
 
localization_priority: Normal
ms.assetid: acc136ef-9946-7c12-a467-9ded732a3549
description: "Returns an integer that represents the Gregorian year in datetime or expression, formatted according to the short date style set by the system's current Region and Language settings."
---

# YEAR Function (VisioShapeSheet)

Returns an integer that represents the Gregorian year in  _datetime_ or  _expression_, formatted according to the short date style set by the system's current Region and Language settings.
  
## Syntax

YEAR(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> | Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**Varies** <br/> |Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Numeric** <br/> |The locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files.  <br/> |
   
### Return value

Integer
  
## Remarks

The time component in  _datetime_ or  _expression_ is discarded. 
  
No rounding is done. If  _datetime_ is missing or cannot be interpreted as a valid date or time, YEAR returns an error. 
  
The YEAR function also accepts a single number value for  _expression_ where the integer portion of the result represents the number of days since December 30, 1899. 
  
## Example 1

YEAR("10/27/2007 13:45:24")
  
Returns 2007.
  
## Example 2

YEAR(DATEVALUE("Dec. 25, 2006") + 7 ed.)
  
Returns 2007.
  
## Example 3

YEAR(35580.6337)
  
Returns 1997.
  

