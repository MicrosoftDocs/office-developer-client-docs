---
title: TableDefs.Delete method (DAO)
TOCTitle: Delete Method
ms:assetid: 130bb50d-17c3-b2ab-9360-0d91d0cee131
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845419(v=office.15)
ms:contentKeyID: 48543358
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# TableDefs.Delete method (DAO)

**Applies to**: Access 2013, Office 2013

Deletes the specified **TableDef** object from the **TableDefs** collection.

## Syntax

*expression* .Delete(***Name***)

*expression* A variable that represents a **TableDefs** object.

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
<td><p>The name of the TableDef to delete.</p></td>
</tr>
</tbody>
</table>


## Remarks

The Delete method is supported only when the **TableDef** object is new and hasn’t been appended to the database, or when the **Updatable** property of the **TableDef** is set to **True**.

