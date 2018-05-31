---
title: "DateWithTimeFromParts function (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
localization_priority: Normal
ms.assetid: aa97cbaa-8b14-42e3-a098-938ebe0769eb
description: "Returns a Date and Time based on a specified year, month, day, and time."
---

# DateWithTimeFromParts function (Access custom web app)

Returns a Date and Time based on a specified year, month, day, and time.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

**DateWithTimeFromParts** (*Year*, *Month*, *Day*, *Hour*, *Minute*, *Second*) 
  
The **DateWithTimeFromParts** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Year*  <br/> |Integer expression specifying a year.  <br/> |
| *Month*  <br/> |Integer expression specifying a month.  <br/> |
| *Day*  <br/> |Integer expression specifying a day.  <br/> |
| *Hour*  <br/> |Integer expression specifying hours.  <br/> |
| *Minute*  <br/> |Integer expression specifying minutes.  <br/> |
| *Second*  <br/> |Integer expression specifying seconds.  <br/> |
   
## Remarks

**DateWithTimeFromParts** returns a fully initialized Date/Time value. If the arguments are not valid, an error is raised. If required arguments are Null, then Null is returned. 
  

