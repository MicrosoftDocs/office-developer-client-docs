---
title: "Month Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
ms.localizationpriority: medium
ms.assetid: 5df43594-a434-4fb7-8109-e5cf0401ae09
description: "Returns an integer that represents the month of the specified date."
---

# Month Function (Access custom web app)

Returns an integer that represents the month of the specified date.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error:
> *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.*
> For cloud storage for Office Online, Office for iOS, and Office for Android, look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage).
  
## Syntax

**Month** (*Date*)
  
The **Month** function contains the following argument.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Date*  <br/> |An expression that can be resolved to a Date/Time value.  <br/> |

## Remarks

**Month** returns the same value as **DatePart** (month, date).
  
If *Date*  contains only a time part, the return value is 1, the base month.
  