---
title: "MONTH Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251467
 
ms.localizationpriority: medium
ms.assetid: e099dbb3-c591-d934-5cfd-7728b10bd8dc
description: "Returns an integer from 1 to 12 that represents a month."
---

# MONTH Function (VisioShapeSheet)

Returns an integer from 1 to 12 that represents a month.
  
## Syntax

MONTH(" ***datetime*** "| ***expression*** [, ***lcid*** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time. |
| _expression_ <br/> |Required  <br/> |**String** <br/> | Any expression that yields a date and time. |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |The locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files. |
   
### Return value

Integer
  
## Remarks

The time component of  _datetime_ or  _expression_ is discarded. 
  
No rounding is done. If the input string is missing or cannot be converted to a valid result, the MONTH function returns an error.
  
The returned value is formatted according to the short date style set by the system's current Regional Settings.
  
The MONTH function also accepts a single number value for  _expression_ where the integer portion of the result represents the number of days since December 30, 1899. 
  
## Example 1

MONTH("May 30, 1999 13:45:24")
  
Returns 5.
  
## Example 2

MONTH(DATEVALUE("May 30, 1999")+7 ed.)
  
Returns 6.
  
## Example 3

MONTH(35580.6337)
  
Returns 5.
  

