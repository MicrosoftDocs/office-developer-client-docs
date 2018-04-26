---
title: "SetWarnings Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm165020
  
localization_priority: Normal
ms.assetid: ff95b919-b1ee-c0a0-851d-71894851bb1d
description: "You can use the SetWarnings action to turn system messages on or off."
---

# SetWarnings Macro Action

You can use the **SetWarnings** action to turn system messages on or off. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **SetWarnings** action has the following argument. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Warnings On** <br/> |Specifies whether system messages are displayed. Click **Yes** (to turn on system messages) or **No** (to turn off system messages) in the **Warnings On** box in the **Action Arguments** section of the Macro Builder Pane. The default is **No**.  <br/> |
   
## Remarks

You can use this action to prevent modal warnings and message boxes from stopping the macro. However, error messages are always displayed. Also, Microsoft Access displays any dialog boxes that require input other than just choosing a button (such as **OK**, **Cancel**, **Yes**, or **No**) — for example, any dialog box that requires you to enter text or select one of several options.
  
Carrying out this action with the **Warnings On** argument set to **No** has the same effect as pressing ENTER whenever a warning or message box is displayed. Typically, an **OK** or **Yes** button is chosen in response to the warning or message. 
  
When the macro finishes, Access automatically turns the display of system messages back on.
  
Often, you'll use this action with the **Echo** action, which hides the results of a macro until it's finished. You can use the **SetWarnings** action to hide the warnings and message boxes as well. 
  
> [!CAUTION]
> Although the **SetWarnings** action can simplify interactions with macros, you must be careful about turning system messages off. In some situations, you won't want to continue a macro if a certain warning message is displayed. Unless you're confident of the outcome of all macro actions, you should avoid using this action. 
  
To run the **SetWarnings** action in a Visual Basic for Applications (VBA) module, use the **SetWarnings** method of the **DoCmd** object. 
  

