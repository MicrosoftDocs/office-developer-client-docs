---
title: "DATEVALUE Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251414
 
localization_priority: Normal
ms.assetid: 514a4053-7729-ec82-c42f-5b780e48cd2a
description: "Returns the date value represented by datetime or expression."
---

# DATEVALUE Function (VisioShapeSheet)

Returns the date value represented by  _datetime_ or  _expression_.
  
## Syntax

DATEVALUE(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time.  <br/> |
| _expression_ <br/> |Required  <br/> |**String** <br/> |Any expression that yields a date and time.  <br/> |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |Specifies the locale identifier to be used in evaluating a non-local datetime. The locale identifier is a number described in the system header files.  <br/> |
   
### Return value

Datetime
  
## Remarks

Any time component in  *datetime*  or  *expression*  is discarded. 
  
If  *datetime*  is missing or cannot be converted to a valid result, DATEVALUE returns a #VALUE! error. 
  
The returned value is displayed using the short date style set by the system's current Regional Settings. 
  
The DATEVALUE function also accepts a single number value for  *expression*  where the integer portion of the result represents the days since December 30, 1899. 
  
## Example 1

DATEVALUE(NOW( ))+5 ed.
  
Returns the date five days from now.
  
## Example 2

DATEVALUE("7/19/1995 12:30")
  
Returns the date.
  
## Example 3

DATEVALUE("May 33, 1997")
  
Returns a #VALUE! error.
  
## Example 4

DATEVALUE(35580.6337)
  
Returns 5/30/1997.
  

