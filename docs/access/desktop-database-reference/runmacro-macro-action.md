---
title: RunMacro macro action
TOCTitle: RunMacro macro action
ms:assetid: 25966f20-8160-0821-b88a-ed08b7786fdc
ms:mtpsurl: https://msdn.microsoft.com/library/Ff191868(v=office.15)
ms:contentKeyID: 48543787
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm43195
f1_categories:
- Office.Version=v15
---

# RunMacro macro action

**Applies to**: Access 2013, Office 2013

You can use the **RunMacro** action to run a macro. The macro can be in a macro group.

You can use this action:

- To run a macro from within another macro.

- To run a macro based on a certain condition.

- To attach a macro to a custom menu command.

## Setting

The **RunMacro** action has the following arguments.

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
<td><p><strong>Macro Name</strong></p></td>
<td><p>The name of the macro to run. The <strong>Macro Name</strong> box in the <strong>Action Arguments</strong> section of the Macro Builder pane shows all macros (and macro groups) in the current database. If the macro is in a macro group, it's listed under the macro group name in the list as <em>macrogroupname</em>.<em>macroname</em>. This is a required argument. If you run a macro containing the <strong>RunMacro</strong> action in a library database, Microsoft Access looks for the macro with this name in the library database and doesn't look for it in the current database.</p></td>
</tr>
<tr class="even">
<td><p><strong>Repeat Count</strong></p></td>
<td><p>The maximum number of times the macro will run. If you leave this argument blank (and the <strong>Repeat Expression</strong> argument is also blank), the macro runs once.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Repeat Expression</strong></p></td>
<td><p>An expression that evaluates to <strong>True</strong> (–1) or <strong>False</strong> (0). The macro stops running if the expression evaluates to <strong>False</strong>. The expression is evaluated each time the macro runs.</p></td>
</tr>
</tbody>
</table>

## Remarks

If you enter a macro group name for the **Macro Name** argument, Access runs the first macro in the macro group.

This action is similar to clicking **Run Macro** on the **Database Tools** tab, selecting a macro, and clicking **OK**. However, this command runs the macro only once, whereas the **RunMacro** action can run a macro as many times as you want.

> [!TIP]
> You can use the **Repeat Count** and **Repeat Expression** arguments to determine how many times the macro runs:
> - If you leave both arguments blank, the macro runs once.
> - If you enter a number for **Repeat Count** but leave **Repeat Expression** blank, the macro runs the specified number of times.
> - If you leave **Repeat Count** blank but enter an expression for **Repeat Expression**, the macro runs until the expression evaluates to **False**.
> - If you enter values for both arguments, the macro runs the number of times specified in **Repeat Count** or until **Repeat Expression** evaluates to **False**, whichever occurs first.

When you run a macro containing the **RunMacro** action, and it reaches the **RunMacro** action, Access runs the called macro. When the called macro has finished, Access returns to the original macro and runs the next action.

> [!NOTE]
> - You can call a macro in the same macro group or in another macro group.
> - You can nest macros. That is, you can run macro A, which in turn calls macro B, and so on. In each case, when the called macro has finished, Access returns to the macro that called it and runs the next action in that macro.

To run the **RunMacro** action in a Visual Basic for Applications (VBA) module, use the **RunMacro** method of the **DoCmd** object.

