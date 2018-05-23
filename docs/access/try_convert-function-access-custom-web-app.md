---
title: "Try_Convert Function (Access custom web app)"
 
 
manager: kelbow
ms.date: 9/5/2017
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ea514f19-4742-4eb4-823d-6f2494668106
description: "Converts a value to a specified data type or returns Null if the conversion is not valid."
---

# Try_Convert Function (Access custom web app)

Converts a value to a specified data type or returns Null if the conversion is not valid.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 **Try_Convert** (*DataType*, *Expression*) 
  
The **Try_Convert** function contains the following arguments. 
  
|**Argument name**|**Description**|
|:-----|:-----|
| *DataType*  <br/> |The data type into which to convert  *Expression*  .  <br/> |
| *Expression*  <br/> |The value to be converted.  <br/> |
   
## Remarks

 **Try_Convert** takes the value passed to it and tries to convert it to the specified  *DataType*  . If the conversion succeeds, **Try_Convert** returns the value as the specified  *DataType*  ; if an error occurs, null is returned. However if you request a conversion that is explicitly not permitted, then **Try_Convert** fails with an error. 
  

