---
title: "ChangeView Macro Action (Access custom web app)"
  
  
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
 
  
ms.localizationpriority: medium
ms.assetid: 7eb20f21-0218-4a2c-9bbc-90218a1e87bc
description: "You can use the ChangeView action to navigate between views in place."
---

# ChangeView Macro Action (Access custom web app)

You can use the **ChangeView** action to navigate between views in place.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Setting

The **ChangeView** action has the following arguments.
  
|**Action argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|Table  <br/> |Yes  <br/> |The name of the table to open. |
|View  <br/> |Yes  <br/> |The name of the view to open. |
|Where  <br/> |No  <br/> |If specified, replaces the Where condition of the object record source. |
|Order By  <br/> |No  <br/> |A string expression that includes the name of the field or fields on which to sort records and the optional ASC or DESC keywords. By default, this argument is blank. |

## Remarks

Any sorting or filtering applied by the user is cleared when the **ChangeView** action is called.
  
The *OrderBy* argument is the name of the field or fields on which you want to sort records. When you use more than one field name, separate the names with a comma (,).
  
When you set the *OrderBy* argument, the records are sorted by default in ascending order.
  