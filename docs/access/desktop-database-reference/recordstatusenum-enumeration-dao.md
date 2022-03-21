---
title: RecordStatusEnum enumeration (DAO)
TOCTitle: RecordStatusEnum Enumeration
ms:assetid: bf4492f2-8d8f-f10f-7a3c-d6296d2ce96b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822784(v=office.15)
ms:contentKeyID: 48547483
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# RecordStatusEnum enumeration (DAO)


**Applies to**: Access 2013, Office 2013

Used with the **RecordStatus** property to indicate the update status of the current record if it is part of a batch update.

<table>
<colgroup>
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dbRecordDBDeleted</p></td>
<td><p>4</p></td>
<td><p>The record has been deleted locally and in the database.</p></td>
</tr>
<tr class="even">
<td><p>dbRecordDeleted</p></td>
<td><p>3</p></td>
<td><p>The record has been deleted, but not yet deleted in the database.</p></td>
</tr>
<tr class="odd">
<td><p>dbRecordModified</p></td>
<td><p>1</p></td>
<td><p>The record has been modified and not updated in the database.</p></td>
</tr>
<tr class="even">
<td><p>dbRecordNew</p></td>
<td><p>2</p></td>
<td><p>The record has been inserted with the <strong>AddNew</strong> method, but not yet inserted into the database.</p></td>
</tr>
<tr class="odd">
<td><p>dbRecordUnmodified</p></td>
<td><p>0</p></td>
<td><p>(Default) The record has not been modified or has been updated successfully.</p></td>
</tr>
</tbody>
</table>

