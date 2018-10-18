---
title: Workspace.OpenDatabase Method (DAO)
TOCTitle: OpenDatabase Method
ms:assetid: dbb93908-ec3e-f3ee-c4ea-cca48340b4d3
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835343(v=office.15)
ms:contentKeyID: 48548108
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Workspace.OpenDatabase Method (DAO)

**Applies to**: Access 2013 | Office 2013

Opens a specified database in a **[Workspace](workspace-object-dao.md)** object and returns a reference to the **[Database](database-object-dao.md)** object that represents it.

## Syntax

*expression* .OpenDatabase(***Name***, ***Options***, ***ReadOnly***, ***Connect***)

*expression* A variable that represents a **Workspace** object.

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
<td><p>the name of an existing Microsoft Access database engine database file, or the data source name (DSN) of an ODBC data source. See the <strong><a href="connection-name-property-dao.md">Name</a></strong> property for more information about setting this value.</p></td>
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


### Return Value

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
> When you access a Microsoft access database engine-connected ODBC data source, you can improve your application's performance by opening a **Database** object connected to the ODBC data source, rather than by linking individual **[TableDef](tabledef-object-dao.md)** objects to specific tables in the ODBC data source.

## Example

This example uses the **OpenDatabase** method to open one Microsoft Access database and two Microsoft Access database engine-connected ODBC databases.

```vb 
Sub OpenDatabaseX() 
 
 Dim wrkAcc As Workspace 
 Dim dbsNorthwind As Database 
 Dim dbsPubs As Database 
 Dim dbsPubs2 As Database 
 Dim dbsLoop As Database 
 Dim prpLoop As Property 
 
 ' Create Microsoft Access Workspace object. 
 Set wrkAcc = CreateWorkspace("", "admin", "", dbUseJet) 
 
 ' Open Database object from saved Microsoft Access database 
 ' for exclusive use. 
 MsgBox "Opening Northwind..." 
 Set dbsNorthwind = wrkAcc.OpenDatabase("Northwind.mdb", _ 
 True) 
 
 ' Open read-only Database object based on information in 
 ' the connect string. 
 MsgBox "Opening pubs..." 
 
 ' Note: The DSN referenced below must be set to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 Set dbsPubs = wrkAcc.OpenDatabase("Publishers", _ 
 dbDriverNoPrompt, True, _ 
 "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 ' Open read-only Database object by entering only the 
 ' missing information in the ODBC Driver Manager dialog 
 ' box. 
 MsgBox "Opening second copy of pubs..." 
 Set dbsPubs2 = wrkAcc.OpenDatabase("Publishers", _ 
 dbDriverCompleteRequired, True, _ 
 "ODBC;DATABASE=pubs;DSN=Publishers;") 
 
 ' Enumerate the Databases collection. 
 For Each dbsLoop In wrkAcc.Databases 
 Debug.Print "Database properties for " & _ 
 dbsLoop.Name & ":" 
 
 On Error Resume Next 
 ' Enumerate the Properties collection of each Database 
 ' object. 
 For Each prpLoop In dbsLoop.Properties 
 If prpLoop.Name = "Connection" Then 
 ' Property actually returns a Connection object. 
 Debug.Print " Connection[.Name] = " & _ 
 dbsLoop.Connection.Name 
 Else 
 Debug.Print " " & prpLoop.Name & " = " & _ 
 prpLoop 
 End If 
 Next prpLoop 
 On Error GoTo 0 
 
 Next dbsLoop 
 
 dbsNorthwind.Close 
 dbsPubs.Close 
 dbsPubs2.Close 
 wrkAcc.Close 
 
End Sub 
 
```

