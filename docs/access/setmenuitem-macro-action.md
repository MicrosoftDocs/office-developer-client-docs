---
title: "SetMenuItem Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vbaac10.chm16614
  
localization_priority: Normal
ms.assetid: 503b3635-e721-1b99-3249-626e5dccdb8a
description: "You can use the SetMenuItem action to set the state of menu items (enabled or disabled, selected or unselected) on custom or global menus on the Add-Ins tab."
---

# SetMenuItem Macro Action

You can use the **SetMenuItem** action to set the state of menu items (enabled or disabled, selected or unselected) on custom or global menus on the **Add-Ins** tab. 
  
> [!NOTE]
> The **SetMenuItem** action works only with custom and global menus created by using menu macros. The **SetMenuItem** action is included in Microsoft Access only for compatibility with previous versions. It does not work with the command bar functionality. However, you can use the **Enabled** and **State** properties in a Visual Basic for Applications (VBA) module to disable or enable and select or unselect items on shortcut menus or custom or global menus. 
  
## Setting

The **SetMenuItem** action has the following arguments. 
  
|**Action argument**|**Description**|
|:-----|:-----|
|**Menu Index** <br/> |The index of the menu that contains the command for which you want to set the state. Enter an integer value, starting from 0, for the index of the desired menu in the custom or global menu. Enter the index value in the **Menu Index** box in the **Action Arguments** section of the Macro Builder pane. The index is relative to the menu's position in the menu macro for the custom or global menu (the position of this menu's **AddMenu** action in the menu macro, counting from 0). The menu's display may be somewhat different, because you can use conditional expressions in the menu macro to hide or display custom menu items. This is a required argument. If you select a menu with this argument and leave the **Command Index** and **Subcommand Index** arguments blank, you can enable or disable the menu name itself. You cannot, however, select or unselect a menu name (Access ignores the **Check** and **Uncheck** settings for the **Flag** argument for menu names).  <br/> |
|**Command Index** <br/> |The index of the command for which you want to set the state. Enter an integer value, starting from 0, for the index of the desired command in the menu selected by the **Menu Index** argument. The index is relative to the command's position in the macro group that defines the selected menu for the custom or global menu (the position of this command's macro in the macro group, counting from 0). The menu's display may be somewhat different, because you can use conditional expressions in the menu's macro group to hide or display custom menu commands.  <br/> |
|**Subcommand Index** <br/> |The index of the subcommand for which you want to set the state. This applies only if the desired command has a submenu. Enter an integer value, starting from 0, for the index of the desired subcommand in the submenu selected by the **Command Index** argument. The index is relative to the subcommand's position in the macro group that defines the selected submenu for the custom or global menu (the position of this subcommand's macro in the macro group, counting from 0).  <br/> |
|**Flag** <br/> |The state you want to set the command or subcommand to. Click **Gray** (to disable the command — it appears dimmed), **Ungray** (to enable it), **Check** (to place a check by the command — typically indicating it has been selected or toggled), or **Uncheck** (to remove the check). The default is **Ungray**.  <br/> |
   
## Remarks

The **SetMenuItem** action works only on a custom or global menu. If the active window does not have a custom or global menu, running a macro containing the **SetMenuItem** action causes a run-time error. 
  
You can use this action to set the state of menu commands and subcommands, but not subcommands of subcommands.
  
To run the **SetMenuItem** action in a Visual Basic for Applications (VBA) module, use the **SetMenuItem** method of the **DoCmd** object. 
  

