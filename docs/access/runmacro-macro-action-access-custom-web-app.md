---
title: "RunMacro Macro Action (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: 59ba365d-cff5-4126-bc22-4d5a37578aab
description: "You can use the RunMacro action to run a user interface (UI) macro."
---

# RunMacro Macro Action (Access custom web app)

You can use the **RunMacro** action to run a user interface (UI) macro. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Setting

The **RunMacro** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Macro Name** <br/> |The name of the UI macro to run.  <br/> |
   
## Remarks

When you run a UI macro containing the **RunMacro** action, and it reaches the **RunMacro** action, Access runs the called UI macro. When the called UI macro has finished, Access returns to the original UI macro and runs the next action. 
  

