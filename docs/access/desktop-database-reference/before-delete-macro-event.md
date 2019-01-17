---
title: Before Delete macro event
TOCTitle: Before Delete macro event
ms:assetid: 1a8d3457-5c59-d13e-ada9-6ecd33dfd5b3
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845672(v=office.15)
ms:contentKeyID: 48543520
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm186077
f1_categories:
- Office.Version=v15
localization_priority: Normal
---

# Before Delete macro event

**Applies to**: Access 2013, Office 2013

The **Before Delete** event occurs when a record is deleted, but before the change is committed.

> [!NOTE]
> The **Before Delete** event is available only in Data Macros.

## Remarks

Use the **Before Delete** event to perform any actions that you want to occur before a record is deleted. The **Before Change** is commonly used to perform validation and to raise custom error messages.

You can access a value in the record to be deleted by using the following syntax:

`[Old].[Field Name]`

For example, to access the value of the QuantityInStock field in the record to be deleted, use the following syntax:

`[Old].[QuantityInStock]`

The values contained in the record to be deleted are deleted permanently when the **Before Delete** event ends.

You can cancel the **Before Delete** event by using the **RaiseError** action. When an error is raised, the changes contained in the **Before Delete** event are discarded.

The following table lists macro commands that can be used in the **Before Delete** event.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Command Type</p></th>
<th><p>Command</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Program Flow</p></td>
<td><p><a href="comment-macro-statement.md">Comment macro statement</a></p></td>
</tr>
<tr class="even">
<td><p>Program Flow</p></td>
<td><p><a href="group-macro-statement.md">Group macro statement</a></p></td>
</tr>
<tr class="odd">
<td><p>Program Flow</p></td>
<td><p><a href="if-then-else-macro-block.md">If...Then...Else macro block</a></p></td>
</tr>
<tr class="even">
<td><p>Data Block</p></td>
<td><p><a href="lookuprecord-data-block.md">LookupRecord macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="clearmacroerror-macro-action.md">ClearMacroError macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="onerror-macro-action.md">OnError macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="raiseerror-macro-action.md">RaiseError macro action</a></p></td>
</tr>
<tr class="even">
<td><p>Data Action</p></td>
<td><p><a href="setlocalvar-macro-action.md">SetLocalVar macro action</a></p></td>
</tr>
<tr class="odd">
<td><p>Data Action</p></td>
<td><p><a href="stopmacro-macro-action.md">StopMacro macro action</a></p></td>
</tr>
</tbody>
</table>


To create a Data macro that captures the **Before Delete** event, use the following steps.

1.  Open the table for which you want to capture the **Before Delete** event.

2.  On the **Table** tab, in the **Before Events** group, select **Before Delete**.

