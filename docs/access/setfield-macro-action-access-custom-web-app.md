---
title: "SetField Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 9ae292b0-fde0-4c2b-ba23-23e90365597d
description: "The SetField action can be used to assign a value to a field."
---

# SetField Macro Action (Access custom web app)

The **SetField** action can be used to assign a value to a field. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **SetField** action is available only in Data Macros. 
  
## Setting

The **SetField** action has the arguments listed in the following table. 
  
|**Argument name**|**Description**|
|:-----|:-----|
|**Name** <br/> |A string that identifies the field.  <br/> |
|**Value** <br/> |An expression that specifies the value to assign to the field.  <br/> |
   
## Remarks

The **SetField** action cannot be used outside of a **[CreateRecord](createrecord-data-block-access-custom-web-app.md)** or **[EditRecord](editrecord-data-block-access-custom-web-app.md)** data block. 
  

