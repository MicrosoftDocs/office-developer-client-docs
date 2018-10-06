---
title: REVOKE Statement (Microsoft Access SQL)
TOCTitle: REVOKE Statement (Microsoft Access SQL)
ms:assetid: 69399fd6-c4e8-f2e2-e5f4-48ae779323f5
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195272(v=office.15)
ms:contentKeyID: 48545409
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277479
f1_categories:
- Office.Version=v15
---

# REVOKE Statement (Microsoft Access SQL)


**Applies to**: Access 2013 | Office 2013

Revokes specific privileges from an existing user or group.

## Syntax

REVOKE {*privilege*\[, *privilege*, …\]} ON {TABLE *table* | OBJECT *object*|

CONTAINTER *container*} FROM {*authorizationname*\[, *authorizationname*, …\]}

The REVOKE statement has these parts:

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
<td><p>The privilege or privileges to be revoked. Privileges are specified using the following keywords: SELECT, DELETE, INSERT, UPDATE, DROP, SELECTSECURITY, UPDATESECURITY, DBPASSWORD, UPDATEIDENTITY, CREATE, SELECTSCHEMA, SCHEMA and UPDATEOWNER.</p></td>
</tr>
<tr class="even">
<td><p><em>table</em></p></td>
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

