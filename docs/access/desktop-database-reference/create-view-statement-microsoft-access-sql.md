---
title: CREATE VIEW statement (Microsoft Access SQL)
TOCTitle: CREATE VIEW statement (Microsoft Access SQL)
ms:assetid: ecaabd75-3081-fd35-830d-5a59b0a51922
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836312(v=office.15)
ms:contentKeyID: 48548519
ms.date: 10/18/2018
mtps_version: v=office.15
ms.localizationpriority: high
---

# CREATE VIEW statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Creates a new view.

> [!NOTE]
> The Microsoft Access database engine does not support the use of CREATE VIEW, or any of the DDL statements, with non-Microsoft Access database engine databases.

## Syntax

CREATE VIEW *view* \[(*field1*\[, *field2*\[, …\]\])\] AS *selectstatement*

The CREATE VIEW statement has these parts:

<table>
<colgroup>
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>view</em></p></td>
<td><p>The name of the view to be created.</p></td>
</tr>
<tr class="even">
<td><p><em>field1</em>, <em>field2</em></p></td>
<td><p>The name of field or fields for the corresponding fields specified in <em>selectstatement</em>.</p></td>
</tr>
<tr class="odd">
<td><p><em>selectstatement</em></p></td>
<td><p>A SQL SELECT statement. For more information, see <a href="select-statement-microsoft-access-sql.md">SELECT statement</a>.</p></td>
</tr>
</tbody>
</table>


## Remarks

The SELECT statement that defines the view cannot be a [SELECT INTO](select-into-statement-microsoft-access-sql.md) statement.

The SELECT statement that defines the view cannot contain any parameters.

The name of the view cannot be the same as the name of an existing table.

If the query defined by the SELECT statement is updatable, the view is also updatable. Otherwise, the view is read-only.

If any two fields in the query defined by the SELECT statement have the same name, the view definition must include a field list specifying unique names for each of the fields in the query.

