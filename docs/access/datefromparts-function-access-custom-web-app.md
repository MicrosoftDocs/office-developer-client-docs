---
title: "DateFromParts function (Access custom web app)" 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
localization_priority: Normal
ms.assetid: 4fa49d5f-12ea-4d14-9a03-28418f01746c
description: "Returns a date value for the specified year, month, and day."
---

# DateFromParts function (Access custom web app)

Returns a date value for the specified year, month, and day.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

**DateFromParts** (*Year*, *Month*, *Day*) 
  
The **DateFromParts** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Year*  <br/> |Integer expression specifying a year.  <br/> |
| *Month*  <br/> |Integer expression specifying a month, from 1 to 12.  <br/> |
| *Day*  <br/> |Integer expression specifying a day.  <br/> |
   
## Remarks

**DateFromParts** returns a date value with the date portion set to the specified year, month and day, and the time portion set to the default. If the arguments are not valid, then an error is raised. If required arguments are null, then NULL is returned. 
  
## Example

The following expression uses the **DateFromParts** function to calculate the first day of the current month. 
  
`DateFromParts(Year(Today()),Month(Today()),1)`



