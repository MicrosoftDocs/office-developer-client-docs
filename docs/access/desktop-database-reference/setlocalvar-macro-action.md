---
title: SetLocalVar macro action
TOCTitle: SetLocalVar macro action
ms:assetid: 8a6af395-0f76-72e2-37f3-2cff22a38b3c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197097(v=office.15)
ms:contentKeyID: 48546190
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm176660
f1_categories:
- Office.Version=v15
localization_priority: Priority
---

# SetLocalVar macro action

**Applies to**: Access 2013, Office 2013

The **SetLocalVar** action creates a temporary variable and set it to a specific value.

## Setting

The **SetLocalVar** action has the following arguments.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p>Yes</p></td>
<td><p>A string that specifies the name of the variable.</p></td>
</tr>
<tr class="even">
<td><p><strong>Expression</strong></p></td>
<td><p>Yes</p></td>
<td><p>An expression that will be used to set the value for this temporary variable. Do not precede the expression with the equal sign (=). You can click the <strong>Build</strong> button to use the <strong>Expression Builder</strong> to set this argument.</p></td>
</tr>
</tbody>
</table>

## Remarks

Variables created by the **SetLocalVar** action can be used only in the macro in which they are defined. Use the **[SetTempVar](settempvar-macro-action.md)** action to define a variable that can be used in another macro, in an event procedure, or on a form or report.

Once a temporary variable has been created, you can refer to it in an expression. For example, if you created a temporary variable named TotalAmount, you could use the variable as the control source for a text box by using the following syntax.

`=[LocalVars]![TotalAmount]`

> [!NOTE]
> In a Data Macro, you do not have to use the LocalVars collection to refer to a variable. For example, if you created a temporary variable in a Data Macro named TotalAmount, you could use the variable as the control source for a text box by using the following syntax: `=[TotalAmount]`.

