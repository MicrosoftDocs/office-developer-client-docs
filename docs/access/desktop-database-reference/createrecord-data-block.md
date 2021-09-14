---
title: CreateRecord data block
TOCTitle: CreateRecord data block
ms:assetid: e18f47f8-2aad-9a14-ad63-ab603a4d5b07
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835671(v=office.15)
ms:contentKeyID: 48548263
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# CreateRecord data block


**Applies to**: Access 2013, Office 2013

You can use the **CreateRecord** data block to create a new record in the specified table.

> [!NOTE]
> The **CreateRecord** data block is available only in Data Macros.

## Setting

The **CreateRecord** data block has the following arguments.

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
<td><p><strong>Create a Record In</strong></p></td>
<td><p>Yes</p></td>
<td><p>The name of the table to create the new record in.</p></td>
</tr>
<tr class="even">
<td><p><strong>Alias</strong></p></td>
<td><p>No</p></td>
<td><p>An string that identifies the record. You can use the record's alias to identify</p></td>
</tr>
</tbody>
</table>


## Remarks

The record created by **CreateRecord** automatically becomes the current record.

After **CreateRecord** statement, you can insert a block of commands that will execute before the new record is committed. The following actions are available in a **CreateRecord** data block.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="cancelrecordchange-macro-action.md">CancelRecordChange macro action</a></p></td>
</tr>
<tr class="even">
<td><p><a href="comment-macro-statement.md">Comment macro statement</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="group-macro-statement.md">Group macro statement</a></p></td>
</tr>
<tr class="even">
<td><p><a href="if-then-else-macro-block.md">If...Then...Else macro statement</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="setfield-macro-action.md">SetField macro action</a></p></td>
</tr>
<tr class="even">
<td><p><a href="setlocalvar-macro-action.md">SetLocalVar macro action</a></p></td>
</tr>
</tbody>
</table>


After the **CreateRecord** action creates a record, use the **SetField** action to specify a value of a field in the new record.

You can use an **If...Then...Else** statment to perform operations based on a condition.

To cancel the creation of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **CreateRecord** data block.

Once the new record is committed, you can use the **LastCreateRecordIdentity** local variable to work with the record. For example, use the following syntax to refer to the AssignedTo field of the most recently created record.

`[LastCreateRecordIdentity].[AssignedTo]`

The **CreateRecord** data block can only be used in the **[After Insert](after-insert-macro-event.md)**, **[After Update](after-update-macro-event.md)**, and **[After Update](after-update-macro-event.md)** data macro events.

