---
title: ALTER USER or DATABASE statement (Microsoft Access SQL)
TOCTitle: ALTER USER or DATABASE statement (Microsoft Access SQL)
ms:assetid: 86ccd296-5171-97e7-683f-cdaab4bde9ab
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197012(v=office.15)
ms:contentKeyID: 48546093
ms.date: 10/18/2018
mtps_version: v=office.15
ms.localizationpriority: medium
---

# ALTER USER or DATABASE statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Changes the password for an existing user or for a database.

## Syntax

ALTER DATABASE PASSWORD *newpassword oldpassword*

ALTER USER *user* PASSWORD *newpassword oldpassword*

The ALTER USER or DATABASE statement has these parts:

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
<td><p><em>newpassword</em></p></td>
<td><p>The new password to be associated with the specified <em>user</em> or <em>database</em> name.</p></td>
</tr>
<tr class="odd">
<td><p><em>oldpassword</em></p></td>
<td><p>The existing password to be associated with the specified <em>user</em> or <em>group</em> name.</p></td>
</tr>
</tbody>
</table>

