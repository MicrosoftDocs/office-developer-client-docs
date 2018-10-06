---
title: ShowToolbar Macro Action
TOCTitle: ShowToolbar Macro Action
ms:assetid: 9e53009b-1e5e-1bee-3bcc-f82dc1b0dc48
ms:mtpsurl: https://msdn.microsoft.com/library/Ff198288(v=office.15)
ms:contentKeyID: 48546649
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm27417
f1_categories:
- Office.Version=v15
---

# ShowToolbar Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **ShowToolbar** action to display or hide a group of commands on the **Add-Ins** tab.


> [!NOTE]
> <P>The <STRONG>ShowToolbar</STRONG> action does not affect shortcut menus.</P>




> [!NOTE]
> <P>This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.</P>



## Setting

The **ShowToolbar** action has the following arguments.

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
<td><p><strong>Toolbar Name</strong></p></td>
<td><p>The name of the command group on the <strong>Add-Ins</strong> tab you want to display or hide. The <strong>Toolbar Name</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder Pane shows all the available groups that can be affected by this action. This is a required argument. If you run a macro containing the <strong>ShowToolbar</strong> action in a library database, Access first looks for the group with this name in the library database, and then in the current database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Show</strong></p></td>
<td><p>Specifies whether to display or hide the group and in which views to display or hide it. The default is <strong>Yes</strong> (show the group at all times). You can select <strong>Yes</strong> to display the group at all times, <strong>Where Appropriate</strong> to display the group only when the appropriate form or report is active, or <strong>No</strong> to hide the group at all times.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can use this action in a macro with conditional expressions to display or hide a group depending on certain conditions.

If you want to show a particular group on just one form or report, you can set the **OnActivate** property of the form or report to the name of a macro that contains a **ShowToolbar** action to show the group. Then set the **OnDeactivate** property of the form or report to the name of a macro that contains a **ShowToolbar** action to hide the group.

The built-in toolbars are not available to display or hide by using this action if you set the **AllowBuiltInToolbars** property to **False** (0) in a Visual Basic for Applications (VBA) module, or if you set the **Allow Built-in Toolbars** option to **False** in VBA by using the **SetOption** method.

To run the **ShowToolbar** action in a VBA module, use the **ShowToolbar** method of the **DoCmd** object.

