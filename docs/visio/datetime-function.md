---
title: "DATETIME Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251413
 
ms.localizationpriority: medium
ms.assetid: 0bf7f757-0b7f-dec1-9709-6612c9ad0d53
description: "Returns the date and time value represented by datetime or expression."
---

# DATETIME Function

Returns the date and time value represented by  _datetime_ or  _expression_.
  
## Syntax

DATETIME(" ** *datetime* ** "| ** *expression* ** [, ** *lcid* ** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _datetime_ <br/> |Required  <br/> |**String** <br/> |Any string commonly recognized as a date and time or a reference to a cell containing a date and time. |
| _expression_ <br/> |Required  <br/> |**String** <br/> |Any expression that yields a date and time. |
| _lcid_ <br/> |Optional  <br/> |**Number** <br/> |Specifies the locale identifier to be used in evaluating a non-local datetime. The locale identifier is a number described in the system header files. |
   
### Return value

Datetime
  
## Remarks

If  *datetime*  is missing or cannot be interpreted as a valid date or time, DATETIME returns a #VALUE! error. 
  
The returned value is formatted according to the short date style and time style in the system's current Regional Settings. 
  
The DATETIME function also accepts a single number value for  *expression*  where the integer portion of the result represents the number of days since December 30, 1899, and the decimal portion represents the fraction of a day since midnight. 
  
## Example 1

DATETIME("May 30, 1997")+5 ed.
  
Returns the value representing 6/4/1997.
  
## Example 2

FORMAT(DATETIME("5/20/1997 14:30:45"),"C")
  
Returns the string "Tuesday, May 20, 1997 2:30:45 PM."
  
## Example 3

DATETIME("1:30 PM July 19")
  
Returns the value representing 7/19/2001 1:30:00 PM (assuming the current year is 2001).
  
## Example 4

DATETIME(35580.6337)
  
Returns the value representing 5/30/1997 3:12:32 PM.
  

