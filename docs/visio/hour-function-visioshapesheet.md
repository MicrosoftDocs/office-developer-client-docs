---
title: "HOUR Function (VisioShapeSheet)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251437
 
ms.localizationpriority: medium
ms.assetid: 2a21d6f9-bad6-92ab-6d36-477bcb9d7f17
description: "Returns an integer, 0 to 23, representing the hour of the day of datetime or expression."
---

# HOUR Function (VisioShapeSheet)

Returns an integer, 0 to 23, representing the hour of the day of _datetime_ or _expression_.
  
## Syntax

HOUR(" **_datetime_** "| **_expression_** [, **_lcid_** ])
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> | A string commonly recognized as a date and time or a reference to a cell containing a date and time. |
| _expression_ <br/> |Required  <br/> |**Varies** <br/> |An expression that yields a date and time. |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> | A locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files. |

## Remarks

The date component in _datetime_ and _expression_ is discarded.
  
No rounding is done. If the _datetime_ is missing or cannot be converted to a valid result, the function returns an error.
  
The returned value is formatted according to the time style set by the system's current Regional Settings.
  
The HOUR function also accepts a single number value for _expression_ where the decimal portion of the result represents the fraction of a day since midnight.
  
## Example 1

HOUR("15:45")
  
Returns 15.
  
## Example 2

HOUR("May 30, 1997 3:45:24 PM")
  
Returns 15.
  
## Example 3

HOUR(0.5)
  
Returns 12.
  
## Example 4

HOUR("5/30/1997")
  
Returns 0.
  