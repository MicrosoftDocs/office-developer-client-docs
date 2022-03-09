---
title: "SetProperty Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: 1e97dd95-23f6-4f49-b3b9-2c7261b3a70d
description: "You can use the SetProperty action to set a property for a control on a view."
---

# SetProperty Macro Action (Access custom web app)

You can use the **SetProperty** action to set a property for a control on a view.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
## Setting

The **SetProperty** action has the arguments listed in the following table.
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Control Name_ <br/> |Type the name of the field or control for which you want to set the property value. Leave this argument blank to set the property for the view. |
| _Property_ <br/> |Select the property that you want to set. See the **Remarks** section in this article for a list of the properties that can be set by using this action. |
| _Value_ <br/> |Type the value that the property is to be set to. For properties whose values are either Yes or No, use **-1** for Yes and **0** for No. |

## Remarks

You can use the **SetProperty** action to set the following properties of a control:
  
- Caption
- Enabled
- ForeColor
- Value
- Visible

If you enter an invalid value for the ***Value*** argument, no error occurs, but Access might change the property to a different value, depending on how it interprets the argument.
  