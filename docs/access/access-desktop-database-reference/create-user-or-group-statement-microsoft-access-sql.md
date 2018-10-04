---
title: CREATE USER or GROUP Statement (Microsoft Access SQL)
TOCTitle: CREATE USER or GROUP Statement (Microsoft Access SQL)
ms:assetid: 62148ce2-0f81-944e-a1ab-edef990fff9f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff194914(v=office.15)
ms:contentKeyID: 48545229
ms.date: 09/18/2015
mtps_version: v=office.15
---

# CREATE USER or GROUP Statement (Microsoft Access SQL)


**Applies to**: Access 2013 | Office 2013

Creates one or more new users or groups.

## Syntax

Create a user:

CREATE USER *user* *password pid* \[, *user* *password pid*, …\]

Create a group:

CREATE GROUP *group* *pid*\[, *group* *pid*, …\]

The CREATE USER or GROUP statement has these parts:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>user</em></p></td>
<td><p>The name of a user to be added to the workgroup information file.</p></td>
</tr>
<tr class="even">
<td><p><em>group</em></p></td>
<td><p>The name of a group to be added to the workgroup information file.</p></td>
</tr>
<tr class="odd">
<td><p><em>password</em></p></td>
<td><p>The password to be associated with the specified <em>user</em> name.</p></td>
</tr>
<tr class="even">
<td><p><em>pid</em></p></td>
<td><p>The personal id.</p></td>
</tr>
</tbody>
</table>


## Remarks

A *user* and a *group* cannot have the same name.

A *password* is required for each *user* or *group* that is created.

