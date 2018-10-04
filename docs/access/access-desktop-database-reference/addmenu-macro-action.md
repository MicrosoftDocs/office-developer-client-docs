---
title: AddMenu Macro Action
TOCTitle: AddMenu Macro Action
ms:assetid: 4eb2afa0-ed1f-41b1-d27f-b3ce7a73d2bb
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193760(v=office.15)
ms:contentKeyID: 48544762
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm37891
f1_categories:
- Office.Version=v15
---

# AddMenu Macro Action


**Applies to**: Access 2013 | Office 2013

This article describes the basic operation of the **AddMenu** macro action.

You can use the **AddMenu** action to create:

  - Custom menus on the **Add-Ins** tab for a particular form or report.

  - A custom shortcut menu for a form, report, or control. The custom shortcut menu replaces the built-in shortcut menu for the form, report, or control.

  - A global shortcut menu. The global shortcut menu replaces the built-in shortcut menu for fields in table and query datasheets, forms, and reports, except where you've added a custom shortcut menu for a form, report, or control.

## Setting

The **AddMenu** action has the following arguments.

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
<td><p><strong>Menu Name</strong></p></td>
<td><p>The name of the menu, for example, &quot;Report Commands&quot; or &quot;Tools&quot;. To create an access key so that you can use the keyboard to choose the menu, type an ampersand (<strong>&amp;</strong>) before the letter you want to be the access key. This letter will be underlined in the menu name on the <strong>Add-Ins</strong> tab.</p></td>
</tr>
<tr class="even">
<td><p><strong>Menu Macro Name</strong></p></td>
<td><p>The name of the macro group that contains the macros for the menu's commands. This is a required argument.</p>

> [!NOTE]
> <P>If you run a macro containing the <STRONG>AddMenu</STRONG> action in a library database, Microsoft Office Access 2007 looks for the macro group with this name in the current database only.</P>


<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Status Bar Text</strong></p></td>
<td><p>The text to display in the status bar when the menu is selected. This argument is ignored for shortcut menus.</p></td>
</tr>
</tbody>
</table>


## Remarks

To run the **AddMenu** action in a Visual Basic for Applications (VBA) module, use the **AddMenu** method of the **DoCmd** object. You can also set the **MenuBar** or **ShortcutMenuBar** property in VBA to create a custom menu on the **Add-Ins** tab or to attach a custom shortcut menu to a form, report, or control. You can set the **ShortcutMenuBar** property of the **Application** object to create a global shortcut menu.

