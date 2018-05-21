---
title: "Update Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 8a8c52c9-81b9-4d10-b42b-e360c67bcf4e
description: "Returns whether an INSERT or UPDATE operation was attempted on the specified field."
---

# Update Function (Access custom web app)

Returns whether an INSERT or UPDATE operation was attempted on the specified field.
  
> [!NOTE]
> The cloud storage feature described in this article is no longer supported in Office 2013 and Office 2016 and may result in the following error: >  *Sorry, we're having server problems, so we can't add \<service\> right now. Please try again later.* > For cloud storage for Office Online, Office for iOS, and Office for Android, you can look into our [Office Cloud Storage Partner Program](https://dev.office.com/programs/officecloudstorage). 
  
## Syntax

 **Update** (*Column*) 
  
The **Update** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *Column*  <br/> |The name of the field to check for an INSERT or UPDATE operation.  <br/> |
   
## Remarks

The **Update** function returns TRUE regardless of whether an INSERT or UPDATE attempt is successful. 
  

