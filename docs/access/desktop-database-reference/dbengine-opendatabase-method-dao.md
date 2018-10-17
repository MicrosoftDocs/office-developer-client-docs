---
title: DBEngine.OpenDatabase Method (DAO)
TOCTitle: OpenDatabase Method
ms:assetid: 49fca321-5955-3e69-64ea-da191536eadb
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193474(v=office.15)
ms:contentKeyID: 48544654
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052979
f1_categories:
- Office.Version=v15
---

# DBEngine.OpenDatabase Method (DAO)


**Applies to**: Access 2013 | Office 2013

Opens a specified database and returns a reference to the **[Database](database-object-dao.md)** object that represents it.

## Syntax

*expression* .OpenDatabase(***Name***, ***Options***, ***ReadOnly***, ***Connect***)

*expression* A variable that represents a **DBEngine** object.

### Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/Optional</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>the name of an existing Microsoft Access database file, or the data source name (DSN) of an ODBC data source. See the <strong><a href="connection-name-property-dao.md">Name</a></strong> property for more information about setting this value.</p></td>
</tr>
<tr class="even">
<td><p>Options</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>Sets various options for the database, as specified in Remarks.</p></td>
</tr>
<tr class="odd">
<td><p>ReadOnly</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p><strong>True</strong> if you want to open the database with read-only access, or <strong>False</strong> (default) if you want to open the database with read/write access.</p></td>
</tr>
<tr class="even">
<td><p>Connect</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>Specifies various connection information, including passwords.</p></td>
</tr>
</tbody>
</table>


<<<<<<< HEAD
### Return Value
=======
### Return value
>>>>>>> master

Database

## Remarks

You can use the following values for the options argument.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Setting</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>True</strong></p></td>
<td><p>Opens the database in exclusive mode.</p></td>
</tr>
<tr class="even">
<td><p><strong>False</strong></p></td>
<td><p>(Default) Opens the database in shared mode.</p></td>
</tr>
</tbody>
</table>


When you open a database, it is automatically added to the **Databases** collection.

Some considerations apply when you use dbname:

  - If it refers to a database that is already open for access by another user, an error occurs.

  - If it doesn't refer to an existing database or valid ODBC data source name, an error occurs.

  - If it's a zero-length string ("") and *connect* is "ODBC;" , a dialog box listing all registered ODBC data source names is displayed so the user can select a database.

To close a database, and thus remove the **Database** object from the **Databases** collection, use the **[Close](connection-close-method-dao.md)** method on the object.


> [!NOTE]
> <P>When you access a Microsoft Access database engine-connected ODBC data source, you can improve your application's performance by opening a <STRONG>Database</STRONG> object connected to the ODBC data source, rather than by linking individual <STRONG><A href="tabledef-object-dao.md">TableDef</A></STRONG> objects to specific tables in the ODBC data source.</P>


