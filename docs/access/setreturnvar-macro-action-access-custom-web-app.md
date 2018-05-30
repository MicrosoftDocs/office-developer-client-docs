---
title: "SetReturnVar Macro action (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview 
localization_priority: Normal
ms.assetid: 57965c84-7a52-4d7c-9c7f-be3d4570576d
description: "The SetReturnVar action creates a return variable and sets it to a specific value."
---

# SetReturnVar Macro action (Access custom web app)

The **SetReturnVar** action creates a return variable and sets it to a specific value. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **SetReturnVar** action is available only in Data Macros. 
  
## Setting

The **SetReturnVar** action has the following arguments. 
  
|**Argument name**|**Required**|**Description**|
|:-----|:-----|:-----|
| _Name_ <br/> |Yes  <br/> |A string that specifies the name of the variable.  <br/> |
| _Expression_ <br/> |Yes  <br/> |An expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal sign (=). You can click the **Build** button to use the **Expression Builder** to set this argument.  <br/> |
   
## Remarks

The **SetReturnVar** action is used to create a **ReturnVar**, which is variable that can be used by macros that call a data macro by using the **RunDataMacro** action. 
  
After a **ReturnVar** is created by the **SetReturnVar** action, the calling macro can use it in an expression. For example, if you created a **ReturnVar** named **UpdateSuccess**, you could use the variable by using the following syntax:
  
`=[ReturnVars]![UpdateSuccess]`

The **SetReturnVar** action can be used only in named data macros. It is not available in data macros that are attached to a data macro event. 
  

