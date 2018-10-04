---
title: RunSQL Macro Action
TOCTitle: RunSQL Macro Action
ms:assetid: 3692142d-f8a8-e194-0b38-051167f46319
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff192476(v=office.15)
ms:contentKeyID: 48544174
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm12983
f1_categories:
- Office.Version=v15
---

# RunSQL Macro Action


**Applies to**: Access 2013 | Office 2013

You can use the **RunSQL** action to run a Access action query by using the corresponding SQL statement. You can also run a data-definition query.


> [!NOTE]
> <P>This action will not be allowed if the database is not trusted. For more information about enabling macros, see the links in the See Also section of this article.</P>



## Setting

The **RunSQL** action has the following arguments.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>SQL Statement</strong></p></td>
<td><p>The SQL statement for the action query or data-definition query you want to run. The maximum length of this statement is 255 characters. This is a required argument.</p></td>
</tr>
<tr class="even">
<td><p><strong>Use Transaction</strong></p></td>
<td><p>Select <strong>Yes</strong> to include this query in a transaction. Select <strong>No</strong> if you don't want to use a transaction. The default is <strong>Yes</strong>. If you select <strong>No</strong> for this argument, the query might run faster.</p></td>
</tr>
</tbody>
</table>


## Remarks

You can use action queries to append, delete, and update records and to save a query's result set as a new table. You can use data-definition queries to create, alter, and delete tables, and to create and delete indexes. You can use the **RunSQL** action to perform these operations directly from a macro without having to use stored queries.

If you need to type an SQL statement longer than 255 characters, use the **RunSQL** method of the **DoCmd** object in a Visual Basic for Applications (VBA) module instead. You can type SQL statements of up to 32,768 characters in VBA.

Access queries are actually SQL statements that are created when you design a query by using the design grid in the Query window. The following table shows the Access action queries and data-definition queries and their corresponding SQL statements.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Query type</p></th>
<th><p>SQL statement</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Action</strong></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Append</p></td>
<td><p>INSERT INTO</p></td>
</tr>
<tr class="odd">
<td><p>Delete</p></td>
<td><p>DELETE</p></td>
</tr>
<tr class="even">
<td><p>Make-table</p></td>
<td><p>SELECT...INTO</p></td>
</tr>
<tr class="odd">
<td><p>Update</p></td>
<td><p>UPDATE</p></td>
</tr>
<tr class="even">
<td><p><strong>Data-definition (SQL-specific)</strong></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Create a table</p></td>
<td><p>CREATE TABLE</p></td>
</tr>
<tr class="even">
<td><p>Alter a table</p></td>
<td><p>ALTER TABLE</p></td>
</tr>
<tr class="odd">
<td><p>Delete a table</p></td>
<td><p>DROP TABLE</p></td>
</tr>
<tr class="even">
<td><p>Create an index</p></td>
<td><p>CREATE INDEX</p></td>
</tr>
<tr class="odd">
<td><p>Delete an index</p></td>
<td><p>DROP INDEX</p></td>
</tr>
</tbody>
</table>


You can also use an IN clause with these statements to modify data in another database.


> [!NOTE]
> <P>To run a select query or crosstab query from a macro, use the View argument of the <STRONG>OpenQuery</STRONG> action to open an existing select query or crosstab query in Datasheet view. You can also run existing action queries and SQL-specific queries in the same way.</P>


