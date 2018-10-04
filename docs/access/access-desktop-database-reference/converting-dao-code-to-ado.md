---
title: Converting DAO Code to ADO
TOCTitle: Converting DAO Code to ADO
ms:assetid: 4720906b-d6b1-aa6d-3b18-ff828d16acae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff193201(v=office.15)
ms:contentKeyID: 48544585
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm5267115
f1_categories:
- Office.Version=v15
---

# Converting DAO Code to ADO


_**Applies to:** Access 2013 | Office 2013_


> [!NOTE]
> <P>Versions of the DAO library prior to 3.6 are not provided or supported in Access.</P>



## DAO to ADO object Map

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>DAO</strong></p></th>
<th><p><strong>ADO(ADODB)</strong></p></th>
<th><p><strong>Note</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DBEngine</p></td>
<td><p>None</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Workspace</p></td>
<td><p>None</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Database</p></td>
<td><p>Connection</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Recordset</p></td>
<td><p>Recordset</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Dynaset-Type</p></td>
<td><p>Keyset</p></td>
<td><p>Retrieves a set of pointers to the records in the recordset</p></td>
</tr>
<tr class="even">
<td><p>Snapshot-Type</p></td>
<td><p>Static</p></td>
<td><p>Both retrieve full records but a Static recordset can be updated.</p></td>
</tr>
<tr class="odd">
<td><p>Table-Type</p></td>
<td><p>Keyset with adCmdTableDirect Option</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Field</p></td>
<td><p>Field</p></td>
<td><p>When referred to in a recordset</p></td>
</tr>
</tbody>
</table>




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>DAO</p></th>
<th><p>ADO</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Open a <strong>Recordset</strong></p></td>
<td><pre><code>Dim db as Database
Dim rs as DAO.Recordset
Set db = CurrentDB()
Set rs = db.OpenRecordset(&quot;Employees&quot;)</code></pre></td>
<td><pre><code>Dim rs as New ADODB.Recordset
rs.Open &quot;Employees&quot;, CurrentProject.Connection, _
         adOpenKeySet, adLockOptimistic</code></pre></td>
</tr>
<tr class="even">
<td><p>Edit a <strong>Recordset</strong></p></td>
<td><pre><code>rs.Edit 
rs(&quot;TextFieldName&quot;) = &quot;NewValue&quot;
rs.Update</code></pre></td>
<td><pre><code>rs(&quot;TextFieldName&quot;) = &quot;NewValue&quot; 
rs.Update</code></pre>

> [!NOTE]
> <P>Moving focus from current record via <STRONG>MoveNext, MoveLast, MoveFirst, MovePrevious</STRONG> without first using the <STRONG>CancelUpdate</STRONG> method will implicitly execute the <STRONG>Update</STRONG> method.</P>


</td>
</tr>
</tbody>
</table>

### About the contributors

**Link provided by** the [UtterAccess](http://www.utteraccess.com) community. UtterAccess is the premier Microsoft Access wiki and help forum.

  - [Choosing between DAO and ADO](http://www.utteraccess.com/wiki/index.php/choosing_between_dao_and_ado)



