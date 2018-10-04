---
title: Workspace.Type Property (DAO)
TOCTitle: Type Property
ms:assetid: 89e59280-d2cd-b6a2-16c5-9f14f42fdd99
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197086(v=office.15)
ms:contentKeyID: 48546177
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Workspace.Type Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**.

## Syntax

*expression* .Type

*expression* A variable that represents a **Workspace** object.

## Remarks

For a **Workspace** object, the possible settings and return values are as follows.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Workspace type</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>dbUseJet</strong></p></td>
<td><p>The <strong>Workspace</strong> is connected to the Microsoft Access database engine.</p></td>
</tr>
<tr class="even">
<td><p><strong>dbUseODBC</strong></p></td>
<td><p>The <strong>Workspace</strong> is connected to an ODBC data source.</p></td>
</tr>
</tbody>
</table>

