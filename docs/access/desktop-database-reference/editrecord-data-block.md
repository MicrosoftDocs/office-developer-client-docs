---
title: EditRecord data block
TOCTitle: EditRecord data block
ms:assetid: fe9f55eb-d7ed-1914-65a9-fa2fcb332b98
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837277(v=office.15)
ms:contentKeyID: 48548940
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# EditRecord data block

**Applies to**: Access 2013, Office 2013

You can use the **EditRecord** data block to change the values contained in an existing record.

> [!NOTE]
> The **EditRecord** data block is available only in Data Macros.


## Setting

The **EditRecord** data block has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Alias</strong></p></td>
<td><p>A string that identifies the record to edit. If the <em>Alias</em> argument is not specified, then the current record is edited.</p></td>
</tr>
</tbody>
</table>

## Remarks

After **EditRecord** statement, you can insert a block of commands that will execute before the changes to the record are comitted. The following actions are available in a **EditRecord** data block.

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

Use the **SetField** action to specify the new values of a field in the edited record.

You can use an **If...Then...Else** statment to perform operations based on a condition.

To cancel the editing of a record, use the **CancelRecordChange** action. This prevents the changes from being committed and exits the **EditRecord** data block.

You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the AssignedTo field of the most recently created record:

`[LastCreateRecordIdentity].[AssignedTo]`

The CreateRecord data block can only be used in the **[After Insert](after-insert-macro-event.md)**, **[After Update](after-update-macro-event.md)**, and **[After Update](after-update-macro-event.md)** data macro events.

