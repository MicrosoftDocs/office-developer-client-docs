---
title: GRANT statement (Microsoft Access SQL)
TOCTitle: GRANT statement (Microsoft Access SQL)
ms:assetid: 50ae97ae-d5be-57e5-d9da-f3fc42f01d83
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193820(v=office.15)
ms:contentKeyID: 48544800
ms.date: 10/18/2018
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277478
f1_categories:
- Office.Version=v15
---

# GRANT statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Grants specific privileges to an existing user or group.

## Syntax

GRANT {*privilege*\[, *privilege*, …\]} ON{TABLE *table* | OBJECT *object*|

CONTAINER *container* } TO {*authorizationname*\[, *authorizationname*, …\]}

The GRANT statement has these parts:

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
<td><p><em>privilege</em></p></td>
<td><p>The privilege or privileges to be granted. Privileges are specified using the following keywords: SELECT, DELETE, INSERT, UPDATE, DROP, SELECTSECURITY, UPDATESECURITY, DBPASSWORD, UPDATEIDENTITY, CREATE, SELECTSCHEMA, SCHEMA, and UPDATEOWNER.</p></td>
</tr>
<tr class="even">
<td><p><em>tablename</em></p></td>
<td><p>Any valid table name.</p></td>
</tr>
<tr class="odd">
<td><p><em>object</em></p></td>
<td><p>This can encompass any non-table object. A stored query (view or procedure) is one example.</p></td>
</tr>
<tr class="even">
<td><p><em>container</em></p></td>
<td><p>The name of a valid container.</p></td>
</tr>
<tr class="odd">
<td><p><em>authorizationname</em></p></td>
<td><p>A user or group name.</p></td>
</tr>
</tbody>
</table>

