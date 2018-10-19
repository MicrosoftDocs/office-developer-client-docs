---
title: ADD USER statement (Microsoft Access SQL)
TOCTitle: ADD USER statement (Microsoft Access SQL)
ms:assetid: 1feb631f-cb8c-14ae-6214-276f1faf1a55
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845862(v=office.15)
ms:contentKeyID: 48543652
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ADD USER statement (Microsoft Access SQL)

**Applies to**: Access 2013 | Office 2013

Adds one or more existing *user*s to an existing *group*.

## Syntax

ADD USER *user*\[, *user*, …\] TO *group*

The ADD USER statement has these parts:

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
</tbody>
</table>


## Remarks

Once a *user* had been added to a *group,* the *user* has all the permissions that have been granted to the *group*.

