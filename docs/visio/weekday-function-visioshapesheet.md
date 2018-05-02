---
title: "WEEKDAY Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251512
 
localization_priority: Normal
ms.assetid: f2625ef8-3bdb-5a8d-48b9-149be0592533
description: "Returns an integer, 1 to 7, representing the weekday in datetime or expression."
---

# WEEKDAY Function (VisioShapeSheet)

Returns an integer, 1 to 7, representing the weekday in  _datetime_ or  _expression_.
  
## Syntax

WEEKDAY(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> | Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**Varies** <br/> |Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Numeric** <br/> |The locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files.  <br/> |
   
### Return Value

Integer
  
## Remarks

The time component in  _datetime_ or  _expression_ is discarded. 
  
The result corresponds to Monday (1) through Sunday (7). No rounding is done. If  _datetime_ is missing or cannot be interpreted as a valid date or time, the function returns a #VALUE! error. 
  
The WEEKDAY function also accepts a single number value for  _expression_ where the integer portion of the result represents the number of days since December 30, 1899. 
  
## Example 1

WEEKDAY("May 30, 1999")
  
Returns 7.
  
## Example 2

WEEKDAY(DATEVALUE("May 30, 1999")+2 ed.)
  
Returns 2.
  
## Example 3

WEEKDAY(35880.6337)
  
Returns 4.
  

