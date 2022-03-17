---
title: Workspace.Type property (DAO)
TOCTitle: Type Property
ms:assetid: 89e59280-d2cd-b6a2-16c5-9f14f42fdd99
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197086(v=office.15)
ms:contentKeyID: 48546177
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Workspace.Type property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**.

## Syntax

*expression* .Type

*expression* A variable that represents a **Workspace** object.

## Remarks

For a **Workspace** object, the possible settings and return values are as follows.

<table>
<colgroup>
<col />
<col />
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

