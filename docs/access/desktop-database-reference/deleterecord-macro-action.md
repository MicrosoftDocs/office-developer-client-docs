---
title: DeleteRecord Macro Action
TOCTitle: DeleteRecord Macro Action
ms:assetid: c656a72c-c037-76a5-dc07-f6eccb6590dd
ms:mtpsurl: https://msdn.microsoft.com/library/Ff823132(v=office.15)
ms:contentKeyID: 48547624
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DeleteRecord Macro Action

**Applies to**: Access 2013 | Office 2013

You can use the **DeleteRecord** action to delete a record.

## Setting

The **CreateRecord** data block has the following arguments.

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
<td><p><strong>Record Alias</strong></p></td>
<td><p>A string that identifies the record to delete. If the <em>Alias</em> argument is not specified, then the current record is deleted.</p></td>
</tr>
</tbody>
</table>

## Remarks

You can use the **LastCreateRecordIdentity** local variable to work with last record created in a **CreateRecord** data block. For example, use the following syntax to refer to the most recently created record:

`[LastCreateRecordIdentity]`

