---
title: "RunDataMacro Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: f6010ac5-6c08-4c1b-a811-ff81b30ed5f0
description: "You can use the RunDataMacro action to run a standalone data macro."
---

# RunDataMacro Macro Action (Access custom web app)

You can use the **RunDataMacro** action to run a standalone data macro. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Setting

The **RunDataMacro** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
| _Macro Name_ <br/> |The name of the data macro to run.  <br/> |
   
## Remarks

When you select the data macro that you want to run in the macro designer, Access determines if the data macro requires parameters. If the data macro requires parameters, text boxes appear where you can type in the arguments.
  
When you run a macro that contains the **RunDataMacro** action and it reaches the **RunDataMacro** action, Access runs the called data macro. When the called data macro has finished, Access returns to the original macro and runs the next action. 
  

