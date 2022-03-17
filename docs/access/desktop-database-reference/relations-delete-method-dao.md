---
title: Relations.Delete method (DAO)
TOCTitle: Delete Method
ms:assetid: e95408d2-9dde-44e7-875e-8f2d4b837cf6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836064(v=office.15)
ms:contentKeyID: 48548438
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Relations.Delete method (DAO)

**Applies to**: Access 2013, Office 2013

Deletes the specified **Relation** from the **Relations** collection.

## Syntax

*expression* .Delete(***Name***)

*expression* A variable that represents a **Relations** object.

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
<td><p>The name of the relation to delete.</p></td>
</tr>
</tbody>
</table>


## Remarks

The **Delete** method is supported only when the **Relation** object is a new, unappended object.

