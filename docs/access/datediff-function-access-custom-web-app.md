---
title: "DateDiff function (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer 
ms.localizationpriority: medium
ms.assetid: 1c58ee87-0f57-4643-be4d-62da815df705
description: "Returns the count of the specified date part boundaries crossed between the specified start date and end date."
---

# DateDiff function (Access custom web app)

Returns the count of the specified date part boundaries crossed between the specified start date and end date.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error:
> *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.*
> For cloud storage for Office Online, Office for iOS, and Office for Android, look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage).
  
## Syntax

**DateDiff** (*DatePart*, *StartDate*, *EndDate*)
  
The **DateDiff** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *DatePart*  <br/> |Is the part of *StartDate* and *EndDate* that specifies the type of boundary crossed. Refer to the Remarks section for the list of valid settings. |
| *StartDate*  <br/> |An expression that can be resolved to a Date/Time value. The *Date*  argument expression, column expression, user-defined variable or string literal. |
| *EndDate*  <br/> |An expression that can be resolved to a Date/Time value. The *Date*  argument expression, column expression, user-defined variable or string literal. |

## Remarks

The following table lists all valid *DatePart*  arguments.
  
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
