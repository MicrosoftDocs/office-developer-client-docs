---
title: "Try_Parse Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ed35263c-b0ad-4269-9caa-c0164015e980
description: "Parses a text value to the specified data type in the culture of the application or returns Null if the conversion is not valid."
---

# Try_Parse Function (Access custom web app)

Parses a text value to the specified data type in the culture of the application or returns Null if the conversion is not valid.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

 **Try_Parse** (*TextExpression*, *DataType*) 
  
The **Try_Parse** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *TextExpression*  <br/> |A text expression representing the formatted value to parse into the specified data type.  <br/> |
| *DataType*  <br/> |The data type into which to parse  *TextExpression*  .  <br/> |
   
## Remarks

Use **Try_Parse** only for converting from string to date/time and number types. For general type conversions, continue to use **Convert**. 
  

