---
title: RecordsetOptionEnum Enumeration (DAO)
TOCTitle: RecordsetOptionEnum Enumeration
ms:assetid: 3a9d8664-dcb6-cb60-7cf6-e229eb699ef1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff192649(v=office.15)
ms:contentKeyID: 48544266
ms.date: 09/18/2015
mtps_version: v=office.15
---

# RecordsetOptionEnum Enumeration (DAO)


_**Applies to:** Access 2013 | Office 2013_

Used with the **OpenRecordset** method to specify characteristics of a new **Recordset** object.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dbAppendOnly</p></td>
<td><p>8</p></td>
<td><p>Allows user to add new records to the dynaset, but prevents user from reading existing records.</p></td>
</tr>
<tr class="even">
<td><p>dbConsistent</p></td>
<td><p>32</p></td>
<td><p>Applies updates only to those fields that will not affect other records in the dynaset (dynaset- and snapshot-type only).</p></td>
</tr>
<tr class="odd">
<td><p>dbDenyRead</p></td>
<td><p>2</p></td>
<td><p>Prevents other users from reading Recordset records (table-type only).</p></td>
</tr>
<tr class="even">
<td><p>dbDenyWrite</p></td>
<td><p>1</p></td>
<td><p>Prevents other users from changing Recordset records.</p></td>
</tr>
<tr class="odd">
<td><p>dbExecDirect</p></td>
<td><p>2048</p></td>
<td><p>Executes the query without first calling the SQLPrepare ODBC function.</p></td>
</tr>
<tr class="even">
<td><p>dbFailOnError</p></td>
<td><p>128</p></td>
<td><p>Rolls back updates if an error occurs.</p></td>
</tr>
<tr class="odd">
<td><p>dbForwardOnly</p></td>
<td><p>256</p></td>
<td><p>Creates a forward-only scrolling snapshot-type Recordset (snapshot-type only).</p></td>
</tr>
<tr class="even">
<td><p>dbInconsistent</p></td>
<td><p>16</p></td>
<td><p>Applies updates to all dynaset fields, even if other records are affected (dynaset- and snapshot-type only).</p></td>
</tr>
<tr class="odd">
<td><p>dbReadOnly</p></td>
<td><p>4</p></td>
<td><p>Opens the Recordset as read-only.</p></td>
</tr>
<tr class="even">
<td><p>dbRunAsync</p></td>
<td><p>1024</p></td>
<td><p>Executes the query asynchronously.</p></td>
</tr>
<tr class="odd">
<td><p>dbSeeChanges</p></td>
<td><p>512</p></td>
<td><p>Generates a run-time error if another user is changing data you are editing (dynaset-type only).</p></td>
</tr>
<tr class="even">
<td><p>dbSQLPassThrough</p></td>
<td><p>64</p></td>
<td><p>Sends an SQL statement to an ODBC database (snapshot-type only).</p></td>
</tr>
</tbody>
</table>

