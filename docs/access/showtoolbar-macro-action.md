---
title: "ShowToolbar Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm27417
  
localization_priority: Normal
ms.assetid: 9e53009b-1e5e-1bee-3bcc-f82dc1b0dc48
description: "You can use the ShowToolbar action to display or hide a group of commands on the Add-Ins tab."
---

# ShowToolbar Macro Action

You can use the **ShowToolbar** action to display or hide a group of commands on the **Add-Ins** tab. 
  
> [!NOTE]
> The **ShowToolbar** action does not affect shortcut menus. 
  
> [!NOTE]
> This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the **See Also** section of this article. 
  
## Setting

The **ShowToolbar** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Toolbar Name** <br/> |The name of the command group on the **Add-Ins** tab you want to display or hide. The **Toolbar Name** box in the **Action Arguments** section of the Macro Builder Pane shows all the available groups that can be affected by this action. This is a required argument. If you run a macro containing the **ShowToolbar** action in a library database, Access first looks for the group with this name in the library database, and then in the current database.  <br/> |
|**Show** <br/> |Specifies whether to display or hide the group and in which views to display or hide it. The default is **Yes** (show the group at all times). You can select **Yes** to display the group at all times, **Where Appropriate** to display the group only when the appropriate form or report is active, or **No** to hide the group at all times.  <br/> |
   
## Remarks

You can use this action in a macro with conditional expressions to display or hide a group depending on certain conditions.
  
If you want to show a particular group on just one form or report, you can set the **OnActivate** property of the form or report to the name of a macro that contains a **ShowToolbar** action to show the group. Then set the **OnDeactivate** property of the form or report to the name of a macro that contains a **ShowToolbar** action to hide the group. 
  
The built-in toolbars are not available to display or hide by using this action if you set the **AllowBuiltInToolbars** property to **False** (0) in a Visual Basic for Applications (VBA) module, or if you set the **Allow Built-in Toolbars** option to **False** in VBA by using the **SetOption** method. 
  
To run the **ShowToolbar** action in a VBA module, use the **ShowToolbar** method of the **DoCmd** object. 
  

