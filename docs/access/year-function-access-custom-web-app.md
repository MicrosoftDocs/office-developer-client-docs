---
title: "Year Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a70751eb-bfde-4f7d-ad90-a1e4cca25dbc
description: "Returns a numeric value that represents the year of the specified date in the Gregorian calendar."
---

# Year Function (Access custom web app)

Returns a numeric value that represents the year of the specified date in the Gregorian calendar.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

 **Year** (*Date*) 
  
The **Year** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Date*  <br/> |An expression that can be resolved to a Date/Time value. The  *Date*  argument expression, column expression, user-defined variable or string literal.  <br/> |
   
## Remarks

Values returned by the **Year**, **Month**, and **Day** functions will be Gregorian values regardless of the display format for the supplied date value. For example, if the display format of the supplied date uses the Hijri calendar, the returned values for the **Year**, **Month**, and **Day** functions will be values associated with the equivalent Gregorian date. 
  

