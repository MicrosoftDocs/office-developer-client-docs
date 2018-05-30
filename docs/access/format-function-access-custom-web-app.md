---
title: "Format Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 550fc235-f0b9-4d8e-805b-ce467821a8c9
description: "Returns a value formatted according to a specified pattern."
---

# Format Function (Access custom web app)

Returns a value formatted according to a specified pattern.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

 **Format** (*Expression*, *Format*) 
  
The **Format** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Expression*  <br/> |Expression of a supported data type to format.  <br/> |
| *Format*  <br/> | A format pattern. The format argument must contain a valid format string, either as a standard format string (for example, "C" or "D"), or as a pattern of custom characters for dates and numeric values (for example, "MMMM dd, yyyy (dddd)"). For more information, see Remarks.  <br/> |
   
## Remarks

For the  *Format*  parameter, you can pass strings that match any of the following patterns: 
  
- [Standard Numeric Format Strings](http://msdn.microsoft.com/en-us/library/dwhawy9k%28v=vs.110%29.aspx)
    
- [Custom Numeric Format Strings](http://msdn.microsoft.com/en-us/library/0c899ak8%28v=vs.110%29.aspx)
    
- [Standard Date and Time Format Strings](http://msdn.microsoft.com/en-us/library/az4se3k1%28v=vs.110%29.aspx)
    
- [Custom Date and Time Format Strings](http://msdn.microsoft.com/en-us/library/8kb3ddd4%28v=vs.110%29.aspx)
    
You cannot use the **Format** function in the following areas of Access 2013 web apps: 
  
- Calculated columns at the table level
    
- UI macros
    
- Expressions in views (for example, in forms)
    

