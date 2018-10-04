---
title: Workspace.OpenConnection Method (DAO)
TOCTitle: OpenConnection Method
ms:assetid: 9d97f298-a2d5-3b91-2efd-57f06fbd4654
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff198249(v=office.15)
ms:contentKeyID: 48546628
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Workspace.OpenConnection Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

## Syntax

*expression* .OpenConnection(***Name***, ***Options***, ***ReadOnly***, ***Connect***)

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
<td><p>A string expression. See the discussion under Remarks.</p></td>
</tr>
<tr class="even">
<td><p>Options</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>sets various options for the connection, as specified in Remarks. Based on this value, the ODBC driver manager prompts the user for connection information such as data source name (DSN), user name, and password.</p></td>
</tr>
<tr class="odd">
<td><p>ReadOnly</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p><strong>True</strong> if the connection is to be opened for read-only access and <strong>False</strong> if the connection is to be opened for read/write access (default).</p></td>
</tr>
<tr class="even">
<td><p>Connect</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>An ODBC connection string. See the <strong><a href="connection-connect-property-dao.md">Connect</a></strong> property for the specific elements and syntax of this string. A prepended &quot;ODBC;&quot; is required.</p></td>
</tr>
</tbody>
</table>


### Return Value

Connection

## Remarks

Use the **OpenConnection** method to establish a connection to an ODBC data source from an ODBCDirect workspace. The **OpenConnection** method is similar but not equivalent to **OpenDatabase**. The main difference is that **OpenConnection** is available only in an ODBCDirect workspace.

If you specify a registered ODBC data source name (DSN) in the connect argument, then the name argument can be any valid string, and will also provide the **Name** property for the **Connection** object. If a valid DSN is not included in the connect argument, then name must refer to a valid ODBC DSN, which will also be the **Name** property. If neither name nor connect contains a valid DSN, the ODBC driver manager can be set (via the options argument) to prompt the user for the required connection information. The DSN supplied through the prompt then provides the **Name** property.

The options argument determines if and when to prompt the user to establish the connection, and whether or not to open the connection asynchronously. You can use one of the following constants.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Constant</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>dbDriverNoPrompt</strong></p></td>
<td><p>The ODBC Driver Manager uses the connection string provided in <em>dbname</em> and <em>connect</em>. If you don't provide sufficient information, a run-time error occurs.</p></td>
</tr>
<tr class="even">
<td><p><strong>dbDriverPrompt</strong></p></td>
<td><p>The ODBC Driver Manager displays the <strong>ODBC Data Sources</strong> dialog box, which displays any relevant information supplied in <em>dbname</em> or <em>connect</em>. The connection string is made up of the DSN that the user selects via the dialog boxes, or, if the user doesn't specify a DSN, the default DSN is used.</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbDriverComplete</strong></p></td>
<td><p>Default. If the <em>connect</em> argument includes all the necessary information to complete a connection, the ODBC Driver Manager uses the string in <em>connect</em>. Otherwise it behaves as it does when you specify <strong>dbDriverPrompt</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>dbDriverCompleteRequired</strong></p></td>
<td><p>This option behaves like <strong>dbDriverComplete</strong> except the ODBC driver disables the prompts for any information not required to complete the connection.</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbRunAsync</strong></p></td>
<td><p>Execute the method asynchronously. This constant may be used with any of the other <em>options</em> constants.</p></td>
</tr>
</tbody>
</table>


**OpenConnection** returns a **Connection** object which contains information about the connection. The **Connection** object is similar to a **[Database](database-object-dao.md)** object. The principal difference is that a **Database** object usually represents a database, although it can be used to represent a connection to an ODBC data source from a Microsoft Access workspace.

## Example

This example uses the **OpenConnection** method with different parameters to open three different **Connection** objects.

``` 
Sub OpenConnectionX() 
 
 Dim wrkODBC As Workspace 
 Dim conPubs As Connection 
 Dim conPubs2 As Connection 
 Dim conPubs3 As Connection 
 Dim conLoop As Connection 
 
 ' Create ODBCDirect Workspace object. 
 Set wrkODBC = CreateWorkspace("NewODBCWorkspace", _ 
 "admin", "", dbUseODBC) 
 
 ' Open Connection object using supplied information in 
 ' the connect string. If this information were 
 ' insufficient, you could trap for an error rather than 
 ' go to an ODBC Driver Manager dialog box. 
 MsgBox "Opening Connection1..." 
 
 ' Note: The DSN referenced below must be set to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 Set conPubs = wrkODBC.OpenConnection("Connection1", _ 
 dbDriverNoPrompt, , _ 
 "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 ' Open read-only Connection object based on information 
 ' you enter in the ODBC Driver Manager dialog box. 
 MsgBox "Opening Connection2..." 
 Set conPubs2 = wrkODBC.OpenConnection("Connection2", _ 
 dbDriverPrompt, True, "ODBC;DSN=Publishers;") 
 
 ' Open read-only Connection object by entering only the 
 ' missing information in the ODBC Driver Manager dialog 
 ' box. 
 MsgBox "Opening Connection3..." 
 Set conPubs3 = wrkODBC.OpenConnection("Connection3", _ 
 dbDriverCompleteRequired, True, _ 
 "ODBC;DATABASE=pubs;DSN=Publishers;") 
 
 ' Enumerate the Connections collection. 
 For Each conLoop In wrkODBC.Connections 
 Debug.Print "Connection properties for " & _ 
 conLoop.Name & ":" 
 
 With conLoop 
 ' Print property values by explicitly calling each 
 ' Property object; the Connection object does not 
 ' support a Properties collection. 
 Debug.Print " Connect = " & .Connect 
 ' Property actually returns a Database object. 
 Debug.Print " Database[.Name] = " & _ 
 .Database.Name 
 Debug.Print " Name = " & .Name 
 Debug.Print " QueryTimeout = " & .QueryTimeout 
 Debug.Print " RecordsAffected = " & _ 
 .RecordsAffected 
 Debug.Print " StillExecuting = " & _ 
 .StillExecuting 
 Debug.Print " Transactions = " & .Transactions 
 Debug.Print " Updatable = " & .Updatable 
 End With 
 
 Next conLoop 
 
 conPubs.Close 
 conPubs2.Close 
 conPubs3.Close 
 wrkODBC.Close 
 
End Sub 
 
```

This example demonstrates the **Connection** object and **Connections** collection by opening a Microsoft Access **Database** object and two ODBCDirect **Connection** objects and listing the properties available to each object.

``` 
Sub ConnectionObjectX() 
 
 Dim wrkAcc as Workspace 
 Dim dbsNorthwind As Database 
 Dim wrkODBC As Workspace 
 Dim conPubs As Connection 
 Dim conPubs2 As Connection 
 Dim conLoop As Connection 
 Dim prpLoop As Property 
 
 ' Open Microsoft Access Database object. 
 Set wrkAcc = CreateWorkspace("NewWorkspace", _ 
 "admin", "", dbUseJet) 
 Set dbsNorthwind = wrkAcc.OpenDatabase("Northwind.mdb") 
 
 ' Create ODBCDirect Workspace object and open Connection 
 ' objects. 
 Set wrkODBC = CreateWorkspace("NewODBCWorkspace", _ 
 "admin", "", dbUseODBC) 
 
 ' Note: The DSNs referenced below must be configured to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 Set conPubs = wrkODBC.OpenConnection("Connection1", , , _ 
 "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 Set conPubs2 = wrkODBC.OpenConnection("Connection2", , _ 
 True, "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 Debug.Print "Database properties:" 
 
 With dbsNorthwind 
 ' Enumerate Properties collection of Database object. 
 For Each prpLoop In .Properties 
 On Error Resume Next 
 Debug.Print " " & prpLoop.Name & " = " & _ 
 prpLoop.Value 
 On Error GoTo 0 
 Next prpLoop 
 End With 
 
 ' Enumerate the Connections collection. 
 For Each conLoop In wrkODBC.Connections 
 Debug.Print "Connection properties for " & _ 
 conLoop.Name & ":" 
 
 With conLoop 
 ' Print property values by explicitly calling each 
 ' Property object; the Connection object does not 
 ' support a Properties collection. 
 Debug.Print " Connect = " & .Connect 
 ' Property actually returns a Database object. 
 Debug.Print " Database[.Name] = " & _ 
 .Database.Name 
 Debug.Print " Name = " & .Name 
 Debug.Print " QueryTimeout = " & .QueryTimeout 
 Debug.Print " RecordsAffected = " & _ 
 .RecordsAffected 
 Debug.Print " StillExecuting = " & _ 
 .StillExecuting 
 Debug.Print " Transactions = " & .Transactions 
 Debug.Print " Updatable = " & .Updatable 
 End With 
 
 Next conLoop 
 
 dbsNorthwind.Close 
 conPubs.Close 
 conPubs2.Close 
 wrkAcc.Close 
 wrkODBC.Close 
 
End Sub 
 
```

