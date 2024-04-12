---
title: "TIMEVALUE Function (VisioShapeSheet)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251507
 
ms.localizationpriority: medium
ms.assetid: 53579e0e-fcec-e745-0207-3861b5efa333
description: "Returns the time value represented by datetime or expression, based on the system's Region and Language settings."
---

# TIMEVALUE Function (VisioShapeSheet)

Returns the time value represented by  _datetime_ or  _expression_, based on the system's Region and Language settings.
  
## Syntax

TIMEVALUE(" ***datetime*** "| ***expression*** [, ***lcid*** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> | Any string commonly recognized as a date and time or a reference to a cell containing a date and time. |
| _expression_ <br/> |Required  <br/> |**Varies** <br/> | Any expression that yields a date and time. |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |The locale identifier to be used in evaluating a nonlocal datetime. The locale identifier is a number described in the system header files. |
   
## Remarks

Any date component in  _datetime_ or  _expression_ is discarded. 
  
If  _datetime_ is missing or cannot be converted to a valid result, this function returns a #VALUE! error. 
  
The TIMEVALUE function also accepts a single number value for  _expression_ where the decimal portion of the result represents the fraction of a day since midnight. 
  
## Example 1

TIMEVALUE("6:00 AM")
  
Returns the value representing 6:00 AM.
  
## Example 2

TIMEVALUE("14:30")+4 eh.+30 em.
  
Returns the value representing 19:00:00.
  
## Example 3

TIMEVALUE("11 AM, July 1, 1997")
  
Returns the value representing 11:00 AM.
  
## Example 4

TIMEVALUE(0.6337)
  
Returns the value representing 15:12:32.
  
## Example 5

TIMEVALUE("7:89")
  
Returns a #VALUE! error.
  

