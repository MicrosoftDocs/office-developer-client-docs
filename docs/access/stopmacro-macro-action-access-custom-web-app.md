---
title: "StopMacro Macro Action (Access custom web app)"
 
 
manager: lindalu
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: af28534b-6f0d-43ee-ae89-ee2f85da1af1
description: "You can use the StopMacro action to stop the currently running macro."
---

# StopMacro Macro Action (Access custom web app)

You can use the **StopMacro** action to stop the currently running macro. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices. 
  
## Setting

The **StopMacro** action doesn't have any arguments. 
  
## Remarks

You typically use this action when a condition makes it necessary to stop the macro. For example, you might create a user interface (UI) macro that opens a view showing the daily order totals for the date entered in the current view. You could use a conditional expression to be sure that the Order Date control on the dialog box contains a valid date. If it doesn't, the **MessageBox** action can display an error message and the **StopMacro** action can stop the UI macro. 
  

