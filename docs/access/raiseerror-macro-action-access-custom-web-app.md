---
title: "RaiseError Macro Action (Access custom web app)"
 
 
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: 5e29bf64-300a-4094-82ff-664e79782d86
description: "The RaiseError action displays a popup window that contains a specified error message."
---

# RaiseError Macro Action (Access custom web app)

The **RaiseError** action displays a popup window that contains a specified error message. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **RaiseError** action is available only in Data Macros. 
  
## Setting

The **RaiseError** action has the following argument. 
  
|**Argument**|**Description**|
|:-----|:-----|
| _Error Description_ <br/> |A string expression that describes the error. |
   
## Remarks

When the **RaiseError** action is called, all of the operations in the current transaction are rolled back. 
  

