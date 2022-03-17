---
title: ForEachRecord data block
TOCTitle: ForEachRecord data block
ms:assetid: be369196-230e-1f92-e36b-667048eef2be
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822743(v=office.15)
ms:contentKeyID: 48547455
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# ForEachRecord data block

**Applies to**: Access 2013, Office 2013

A **ForEachRecord** data block repeats a set of statements for each record in a domain.

> [!NOTE]
> The **ForEachRecord** data block is available only in Data Macros.

## Setting

The **ForEachRecord** action has the following arguments.

<table>
<colgroup>
<col />
<col />
<col />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>In</strong></p></td>
<td><p>Yes</p></td>
<td><p>A string that identifies the domain of records to operate on. The <em>In</em> argument can contain the name of the table, a select query, or a SQL statement.</p><p><strong>NOTE</strong>: The specified domain cannot include data stored in a linked table or ODBC data source.</p></td>
</tr>
<tr class="even">
<td><p><strong>Where Condition</strong></p></td>
<td><p>No</p></td>
<td><p>A string expression used to restrict the range of data on which the <strong>ForEachRecord</strong> data block is performed. For example, criteria is often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria is omitted, the <strong>ForEachRecord</strong> data block operates on the entire domain specified by the <em>In</em> argument. Any field that is included in criteria must also be a field in <em>In</em>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Alias</strong></p></td>
<td><p>No</p></td>
<td><p>A string that provides an alternative name for the domain specified by the <em>In</em> argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references.If <em>Alias</em> is not specified, the table or query name will be used as the alias.</p></td>
</tr>
</tbody>
</table>


## Remarks

Use the **[ExitForEachRecord](exitforeachrecord-macro-action.md)** action to exit a **ForEachRecord** data block immediately.

