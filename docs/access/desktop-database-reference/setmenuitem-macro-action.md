---
title: SetMenuItem Macro Action
TOCTitle: SetMenuItem Macro Action
ms:assetid: 503b3635-e721-1b99-3249-626e5dccdb8a
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193803(v=office.15)
ms:contentKeyID: 48544789
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm16614
f1_categories:
- Office.Version=v15
---

# SetMenuItem Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **SetMenuItem** action to set the state of menu items (enabled or disabled, selected or unselected) on custom or global menus on the **Add-Ins** tab.


> [!NOTE]
> <P>The <STRONG>SetMenuItem</STRONG> action works only with custom and global menus created by using menu macros. The <STRONG>SetMenuItem</STRONG> action is included in Microsoft Access only for compatibility with previous versions. It does not work with the command bar functionality. However, you can use the <STRONG>Enabled</STRONG> and <STRONG>State</STRONG> properties in a Visual Basic for Applications (VBA) module to disable or enable and select or unselect items on shortcut menus or custom or global menus.</P>



## Setting

The **SetMenuItem** action has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Menu Index</strong></p></td>
<td><p>The index of the menu that contains the command for which you want to set the state. Enter an integer value, starting from 0, for the index of the desired menu in the custom or global menu. Enter the index value in the <strong>Menu Index</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane. The index is relative to the menu's position in the menu macro for the custom or global menu (the position of this menu's <strong>AddMenu</strong> action in the menu macro, counting from 0). The menu's display may be somewhat different, because you can use conditional expressions in the menu macro to hide or display custom menu items. This is a required argument. If you select a menu with this argument and leave the <strong>Command Index</strong> and <strong>Subcommand Index</strong> arguments blank, you can enable or disable the menu name itself. You cannot, however, select or unselect a menu name (Access ignores the <strong>Check</strong> and <strong>Uncheck</strong> settings for the <strong>Flag</strong> argument for menu names).</p></td>
</tr>
<tr class="even">
<td><p><strong>Command Index</strong></p></td>
<td><p>The index of the command for which you want to set the state. Enter an integer value, starting from 0, for the index of the desired command in the menu selected by the <strong>Menu Index</strong> argument. The index is relative to the command's position in the macro group that defines the selected menu for the custom or global menu (the position of this command's macro in the macro group, counting from 0). The menu's display may be somewhat different, because you can use conditional expressions in the menu's macro group to hide or display custom menu commands.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Subcommand Index</strong></p></td>
<td><p>The index of the subcommand for which you want to set the state. This applies only if the desired command has a submenu. Enter an integer value, starting from 0, for the index of the desired subcommand in the submenu selected by the <strong>Command Index</strong> argument. The index is relative to the subcommand's position in the macro group that defines the selected submenu for the custom or global menu (the position of this subcommand's macro in the macro group, counting from 0).</p></td>
</tr>
<tr class="even">
<td><p><strong>Flag</strong></p></td>
<td><p>The state you want to set the command or subcommand to. Click <strong>Gray</strong> (to disable the command — it appears dimmed), <strong>Ungray</strong> (to enable it), <strong>Check</strong> (to place a check by the command — typically indicating it has been selected or toggled), or <strong>Uncheck</strong> (to remove the check). The default is <strong>Ungray</strong>.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **SetMenuItem** action works only on a custom or global menu. If the active window does not have a custom or global menu, running a macro containing the **SetMenuItem** action causes a run-time error.

You can use this action to set the state of menu commands and subcommands, but not subcommands of subcommands.

To run the **SetMenuItem** action in a Visual Basic for Applications (VBA) module, use the **SetMenuItem** method of the **DoCmd** object.

