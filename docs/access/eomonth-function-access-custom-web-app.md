---
title: "EOMonth Function (Access custom web app)"
  
  
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
 
  
ms.localizationpriority: medium
ms.assetid: df98bcca-152b-49f2-b4e1-35d68008fb8f
description: "Returns the last day of the month before or specified number of months."
---

# EOMonth Function (Access custom web app)

Returns the last day of the month before or specified number of months.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error:
> *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.*
> For cloud storage for Office Online, Office for iOS, and Office for Android, look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage).
  
## Syntax

 **EOMonth** (*Date*, *NumberOfMonth*)
  
The **EOMonth** contains the following arguments.
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Date*  <br/> |The start date in Date/Time format, or in an accepted text representation of a date. |
| *NumberOfMonth*  <br/> |A number representing the number of months before or after the *Date*. |

## Remarks

If *Date*  is not a valid date, **EOMonth** returns an error.
  
If *Date*  plus  *NumberOfMonth*  yields an invalid date, **EOMonth** returns an error.
  