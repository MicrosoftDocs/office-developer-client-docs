---
title: "GoToControl Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
localization_priority: Normal
ms.assetid: 6c286821-67d6-4d96-973a-bca7934c7672
description: "You can use the GoToControl action to move the focus to the specified control in the current record of the open view."
---

# GoToControl Macro Action (Access custom web app)

You can use the **GoToControl** action to move the focus to the specified control in the current record of the open view. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Setting

The **GoToControl** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Control Name** <br/> |The name of the field or control where you want the focus. This is a required argument.  <br/> |
   
## Remarks

You can use this action when you want a particular field or control to have the focus. You can also use this action to navigate in a form according to certain conditions. For example, if the user enters No in a Married control on a health insurance form, the focus can automatically skip the Spouse/partner Name control and move to the next control.
  

