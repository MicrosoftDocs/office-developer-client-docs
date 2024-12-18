---
title: "DateAdd function (Access custom web app)" 
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 7174c585-86e1-42a3-bb7f-d6641001b0f2
description: "Returns a specified date with the specified number interval (positive or negative integer) added to a specified date part of that date."
---

# DateAdd function (Access custom web app)

Returns a specified date with the specified number interval (positive or negative integer) added to a specified date part of that date.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error:
> *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.*
> For cloud storage for Office Online, Office for iOS, and Office for Android, look into our [Office Cloud Storage Partner Program](/microsoft-365/cloud-storage-partner-program/online/overview).
  
## Syntax

**DateAdd** (*DatePart*, *Number*, *Date*)
  
The **DateAdd** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *DatePart*  <br/> |The part of *Date* to which an integer number is added. Refer to the Remarks section for the list of valid settings. |
| *Number*  <br/> |Is an expression that can be resolved to an integer that is added to a *DatePart* of *Date*. If you specify a value with a decimal fraction, the fraction is truncated. |
| *Date*  <br/> |An expression that can be resolved to a Date/Time value. The *Date* argument expression, column expression, user-defined variable or string literal. |

## Remarks

The following table lists all valid *DatePart* arguments.
  
|***DatePart***|
|:-----|
|**year** <br/> |
|**quarter** <br/> |
|**month** <br/> |
|**dayofyear** <br/> |
|**day** <br/> |
|**week** <br/> |
|**hour** <br/> |
|**minute** <br/> |
|**second** <br/> |
|**millisecond** <br/> |

## Example

The following expression calculates the last day of the current month.
  
`DateAdd(Day,-1,DateAdd(Month,DateDiff(Month,0,Today())+1,0))`

The following expression calculates the last day of the previous month.
  
`DateAdd(Day,-1,DateAdd(Month,DateDiff(Month,0,Today()),0))`
