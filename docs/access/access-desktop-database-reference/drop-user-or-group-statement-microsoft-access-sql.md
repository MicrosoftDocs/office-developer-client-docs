---
title: DROP USER or GROUP Statement (Microsoft Access SQL)
TOCTitle: DROP USER or GROUP Statement (Microsoft Access SQL)
ms:assetid: 46bc5916-556b-17df-2f4c-8fd7bbd21ef7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff193192(v=office.15)
ms:contentKeyID: 48544575
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DROP USER or GROUP Statement (Microsoft Access SQL)


_**Applies to:** Access 2013 | Office 2013_

Deletes one or more existing *user*s or *group*s, or removes one or more existing *user*s from an existing *group*.

## Syntax

Delete one or more *user*s or remove one or more *user*s from a *group*:

DROP USER *user*\[, *user*, …\] \[FROM *group*\]

Delete one or more *group*s:

DROP GROUP *group*\[, *group*, …\]

The DROP USER or GROUP statement has these parts:

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
<td><p>The name of a user to be removed from the workgroup information file.</p></td>
</tr>
<tr class="even">
<td><p><em>group</em></p></td>
<td><p>The name of a group to be removed from the workgroup information file.</p></td>
</tr>
</tbody>
</table>


## Remarks

If the FROM keyword is used in the DROP USER statement, then each of the *user*s listed in the statement will be removed from the *group* specified following the FROM keyword. However, the *user*s themselves will not be deleted.

The DROP GROUP statement will delete the specified *group*(s). The *user*s who are members of the *group*(s) will not be affected, but they will no longer be members of the deleted *group*(s).

