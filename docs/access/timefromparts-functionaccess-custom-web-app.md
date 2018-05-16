---
title: "TimeFromParts Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 7f631b7e-6e3c-46dc-a05f-6a07f9a91268
description: "Returns a time value based on specified parts."
---

# TimeFromParts Function (Access custom web app)

Returns a time value based on specified parts.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

 **TimeFromParts** (  *Hour*  ,  *Minute*  ,  *Second*  ) 
  
The **TimeFromParts** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Hour*  <br/> |Integer expression specifying hours.  <br/> |
| *Minute*  <br/> |Integer expression specifying minutes.  <br/> |
| *Second*  <br/> |Integer expression specifying seconds.  <br/> |
   
## See also

 **TimeFromParts** returns a fully initialized time value. If the arguments are invalid, then an error is raised. If any of the parameters are null, null is returned. 
  

