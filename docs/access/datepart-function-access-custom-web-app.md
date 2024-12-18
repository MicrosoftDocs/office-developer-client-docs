---
title: "DatePart function (Access custom web app)" 
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer 
ms.localizationpriority: medium
ms.assetid: 8936f0b6-f9b2-44ef-bf90-e482b64611cd
description: "Returns a numeric value that represents the specified date part of the specified date."
---

# DatePart function (Access custom web app)

Returns a numeric value that represents the specified date part of the specified date.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error:
> *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.*
> For cloud storage for Office Online, Office for iOS, and Office for Android, look into our [Office Cloud Storage Partner Program](/microsoft-365/cloud-storage-partner-program/online/overview).
  
## Syntax

**DatePart** (*DatePart*, *Date*)
  
The **DatePart** function contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *DatePart*  <br/> |The part of *Date* (a date or time value) for which an integer will be returned. Refer to the Remarks section for the list of valid abbreviations. |
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
|**weekday** <br/> |
|**hour** <br/> |
|**minute** <br/> |
|**second** <br/> |
|**millisecond** <br/> |
