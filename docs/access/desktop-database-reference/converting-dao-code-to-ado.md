---
<<<<<<< HEAD
title: Converting DAO Code to ADO
TOCTitle: Converting DAO Code to ADO
ms:assetid: 4720906b-d6b1-aa6d-3b18-ff828d16acae
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193201(v=office.15)
ms:contentKeyID: 48544585
ms.date: 09/18/2015
=======
title: Convert DAO code to ADO
TOCTitle: Convert DAO code to ADO
ms:assetid: 4720906b-d6b1-aa6d-3b18-ff828d16acae
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193201(v=office.15)
ms:contentKeyID: 48544585
ms.date: 10/16/2018
>>>>>>> master
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm5267115
f1_categories:
- Office.Version=v15
---

<<<<<<< HEAD
# Converting DAO Code to ADO
=======
# Convert DAO code to ADO
>>>>>>> master

**Applies to**: Access 2013 | Office 2013

> [!NOTE]
> Versions of the DAO library prior to 3.6 are not provided or supported in Access.

## DAO to ADO object map

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>DAO</strong></p></th>
<<<<<<< HEAD
<th><p><strong>ADO(ADODB)</strong></p></th>
=======
<th><p><strong>ADO (ADODB)</strong></p></th>
>>>>>>> master
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
<<<<<<< HEAD
<td><p>Retrieves a set of pointers to the records in the recordset</p></td>
=======
<td><p>Retrieves a set of pointers to the records in the recordset.</p></td>
>>>>>>> master
</tr>
<tr class="even">
<td><p>Snapshot-Type</p></td>
<td><p>Static</p></td>
<<<<<<< HEAD
<td><p>Both retrieve full records but a Static recordset can be updated.</p></td>
</tr>
<tr class="odd">
<td><p>Table-Type</p></td>
<td><p>Keyset with adCmdTableDirect Option</p></td>
=======
<td><p>Both retrieve full records, but a Static recordset can be updated.</p></td>
</tr>
<tr class="odd">
<td><p>Table-Type</p></td>
<td><p>Keyset with adCmdTableDirect option.</p></td>
>>>>>>> master
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Field</p></td>
<td><p>Field</p></td>
<<<<<<< HEAD
<td><p>When referred to in a recordset</p></td>
=======
<td><p>When referred to in a recordset.</p></td>
>>>>>>> master
</tr>
</tbody>
</table>

<br/>
<br/>

### DAO

#### Open a Recordset

```vb
 Dim db as Database
 Dim rs as DAO.Recordset
 Set db = CurrentDB()
 Set rs = db.OpenRecordset("Employees")
```

#### Edit a Recordset

```vb
 rs.Edit 
 rs("TextFieldName") = "NewValue"
 rs.Update
```

### ADO

#### Open a Recordset

```vb
 Dim rs as New ADODB.Recordset
 rs.Open "Employees", CurrentProject.Connection, _
         adOpenKeySet, adLockOptimistic
```

#### Edit a Recordset

```vb
 rs("TextFieldName") = "NewValue" 
 rs.Update
```


> [!NOTE]
<<<<<<< HEAD
> Moving focus from current record via **MoveNext, MoveLast, MoveFirst, MovePrevious** without first using the **CancelUpdate** method will implicitly execute the **Update** method.
=======
> Moving focus from current record via **MoveNext, MoveLast, MoveFirst, MovePrevious** without first using the **CancelUpdate** method implicitly executes the **Update** method.
>>>>>>> master

### About the contributors

**Link provided by** the [UtterAccess](https://www.utteraccess.com) community. UtterAccess is the premier Microsoft Access wiki and help forum.

- [Choosing between DAO and ADO](https://www.utteraccess.com/wiki/index.php/choosing_between_dao_and_ado)

<<<<<<< HEAD

=======
<br/>
>>>>>>> master

