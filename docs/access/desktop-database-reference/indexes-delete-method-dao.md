---
title: Indexes.Delete method (DAO)
TOCTitle: Delete Method
ms:assetid: 8d3c3221-3b2e-15ba-32ff-f2dfc592d82c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197351(v=office.15)
ms:contentKeyID: 48546252
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Indexes.Delete method (DAO)

**Applies to**: Access 2013, Office 2013

Deletes the specified **Index** from the **Indexes** collection.

## Syntax

*expression* .Delete(***Name***)

*expression* A variable that represents an **Indexes** object.

## Parameters

<table>
<colgroup>
<col />
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/optional</p></th>
<th><p>Data type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>The name of the index to delete.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **Delete** method is supported only when the **Index** object is new and hasn’t been appended to the database.

