---
title: Using ActiveX Data Objects
TOCTitle: Using ActiveX Data Objects
ms:assetid: 64055c45-7a27-2296-468a-015362898329
ms:mtpsurl: https://msdn.microsoft.com/library/Ff194969(v=office.15)
ms:contentKeyID: 48545279
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm5285627
f1_categories:
- Office.Version=v15
---

# Using ActiveX Data Objects


**Applies to**: Access 2013, Office 2013

Microsoft Access provides three object models to use in the creation, maintaining and managing of your Access databases and their related data by using Visual Basic.

## Microsoft ActiveX Data Objects (ADO)

ADO contains the objects needed to create, maintain, and delete records in a given datasource.

## Microsoft ADO Ext. for DDL and Security (ADOX)

ADOX provides the Data Definition Language(DDL) objects needed to create a new database and its contained objects in addition to the objects needed to manage security.

**Microsoft Jet and Replication Objects 2.5 Library (JRO)**

Since ADO objects were designed to work with many databases in addition to Microsoft Jet databases, functionality specific to Jet was broken out into the JRO library.

The following table lists the functionality provided by each compared to DAO.

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Functionality</p></th>
<th><p>DAO</p></th>
<th><p>ADO1</p></th>
<th><p>ADOX2</p></th>
<th><p>JRO<br />
(MDB's Only)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Create Recordsets</p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Edit Startup properties</p></td>
<td><p>X</p></td>
<td><p>X**</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Support ANSI92 SQL***</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Create Tables</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Create New Database</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X*</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Edit Existing Table properties</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Create table relationships</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X*</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Edit security settings</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X*</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Support for Compression attribute for column data</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Edit stored, basic SQL queries or views</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p>X*</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Create permanent queries that are accessible only through code.</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X*</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Create queries accessible through database container/UI and code.</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Compact/Encode database</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X4</p></td>
</tr>
<tr class="even">
<td><p>Refresh Cache</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X</p></td>
</tr>
<tr class="odd">
<td><p>Make Database Replicable</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X3</p></td>
</tr>
<tr class="even">
<td><p>Make Database Replicas</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X3</p></td>
</tr>
<tr class="odd">
<td><p>Synchronize Replicas</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>X3</p></td>
</tr>
<tr class="even">
<td><p>Edit Database properties</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Create custom database properties</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Edit table column properties</p></td>
<td><p>X</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


\* Only available when working with Microsoft Access databases. Future versions of the SQL Provider may provide this functionality in Microsoft Access projects (.adp).

\*\* Only available when working with Access projects.

\*\*\* Though the Access database engine does support some ANSI 92 SQL it is not yet fully ANSI92 compliant.

1 Uses **Connection** object to reference to database

2 Uses **Catalog** object to reference database

3 Uses **Replica** object to reference database

4 Uses **JetEngine** object to reference database


> [!NOTE]
> <P>Unlike DAO, ADO and ADOX objects can perform the marked actions in databases other then Jet as long as the provider for those databases supports that action.</P>


