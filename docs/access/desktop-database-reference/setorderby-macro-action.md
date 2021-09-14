---
title: SetOrderBy macro action
TOCTitle: SetOrderBy macro action
ms:assetid: 78f65ce9-b56f-f476-3bd6-f3307bc22a08
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196152(v=office.15)
ms:contentKeyID: 48545765
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm98639
f1_categories:
- Office.Version=v15
ms.localizationpriority: medium
---

# SetOrderBy macro action


**Applies to**: Access 2013, Office 2013

You can use the **SetOrderBy** action to specify how you want to sort records in a form, report, table, or query result.

## Setting

The **SetOrderBy** action has the following arguments.

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
<td><p><strong>Order By</strong></p></td>
<td><p>A string expression that includes the name of the field or fields on which to sort records and the optional ASC or DESC keywords.</p></td>
</tr>
<tr class="even">
<td><p><strong>Control Name</strong></p></td>
<td><p>If provided and the active object is a form or report, the name of the control that corresponds to the subform or subreport that will be sorted. If empty and the active object is a form or report, the parent form or report is sorted..</p></td>
</tr>
</tbody>
</table>


## Remarks

When you run this macro action, the sort is applied to the table, form, report or datasheet (query result) that is active and has the focus.

The Order By argument is the name of the field or fields on which you want to sort records. When you use more than one field name, separate the names with a comma (,). The **OrderBy** property of the active object is used to save the ordering value and apply it at a later time. OrderBy values are saved with the objects in which they are created. They are automatically loaded when the object is opened, but they aren't automatically applied.

When you set the Order By argument by entering one or more field names and then run the macro, the records are sorted by default in ascending order.

To sort records in descending order, type DESC at the end of the Order By argument expression. For example, to sort customer records in descending order by contact name, set the Order By argument to "ContactName DESC". To sort names by LastName descending, and FirstName ascending, set the Order By argument to "LastName DESC, FirstName ASC".

