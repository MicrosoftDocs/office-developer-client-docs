---
title: Database.Execute method (DAO)
TOCTitle: Execute method
ms:assetid: 9294d530-f70f-e1ed-3990-ce128de4378b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197654(v=office.15)
ms:contentKeyID: 48546378
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: high
---

# Database.Execute method (DAO)

**Applies to**: Access 2013, Office 2013

Runs an action query or executes an SQL statement on the specified object.

## Syntax

*expression* .Execute(***Query***, ***Options***)

*expression* A variable that represents a **Database** object.

## Parameters

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
<th><p>Required/optional</p></th>
<th><p>Data type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Query</em></p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><em>Options</em></p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Remarks

You can use the following **[RecordsetOptionEnum](recordsetoptionenum-enumeration-dao.md)** constants for options.

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
<td><p><strong>dbDenyWrite</strong></p></td>
<td><p>Denies write permission to other users (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbInconsistent</strong></p></td>
<td><p>(Default) Executes inconsistent updates (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbConsistent</strong></p></td>
<td><p>Executes consistent updates (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSQLPassThrough</strong></p></td>
<td><p>Executes an SQL pass-through query. Setting this option passes the SQL statement to an ODBC database for processing (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbFailOnError</strong></p></td>
<td><p>Rolls back updates if an error occurs (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbSeeChanges</strong></p></td>
<td><p>Generates a run-time error if another user is changing data you are editing (Microsoft Access workspaces only).</p></td>
</tr>
<tr class="odd">
<td><p><strong>dbRunAsync</strong></p></td>
<td><p>Executes the query asynchronously (ODBCDirect Connection and QueryDef objects only).</p></td>
</tr>
<tr class="even">
<td><p><strong>dbExecDirect</strong></p></td>
<td><p>Executes the statement without first calling SQLPrepare ODBC API function (ODBCDirect Connection and QueryDef objects only).</p></td>
</tr>
</tbody>
</table>


> [!NOTE]
> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.

> [!NOTE]
> The constants **dbConsistent** and **dbInconsistent** are mutually exclusive. You can use one or the other, but not both in a given instance of **OpenRecordset**. Using both **dbConsistent** and **dbInconsistent** causes an error.

The **Execute** method is valid only for action queries. If you use **Execute** with another type of query, an error occurs. Because an action query doesn't return any records, **Execute** doesn't return a **Recordset**. (Executing an SQL pass-through query in an ODBCDirect workspace will not return an error if a **Recordset** isn't returned.)

Use the **RecordsAffected** property of the **Connection**, **Database**, or **QueryDef** object to determine the number of records affected by the most recent **Execute** method. For example, **RecordsAffected** contains the number of records deleted, updated, or inserted when executing an action query. When you use the **Execute** method to run a query, the **RecordsAffected** property of the **QueryDef** object is set to the number of records affected.

In a Microsoft Access workspace, if you provide a syntactically correct SQL statement and have the appropriate permissions, the **Execute** method won't fail — even if not a single row can be modified or deleted. Therefore, always use the **dbFailOnError** option when using the **Execute** method to run an update or delete query. This option generates a run-time error and rolls back all successful changes if any of the records affected are locked and can't be updated or deleted.

In earlier versions of the Microsoft Jet database engine, SQL statements were automatically embedded in implicit transactions. If part of a statement executed with **dbFailOnError** failed, the entire statement would be rolled back. To improve performance, these implicit transactions were removed starting with version 3.5. If you are updating older DAO code, be sure to consider using explicit transactions around **Execute** statements.

For best performance in a Microsoft Access workspace, especially in a multiuser environment, nest the **Execute** method inside a transaction. Use the **BeginTrans** method on the current **Workspace** object, then use the **Execute** method, and complete the transaction by using the **CommitTrans** method on the **Workspace**. This saves changes on disk and frees any locks placed while the query is running.

## Example

This example demonstrates the **Execute** method when run from both a **QueryDef** object and a **Database** object. The ExecuteQueryDef and PrintOutput procedures are required for this procedure to run.

```vb
    Sub ExecuteX() 
     
     Dim dbsNorthwind As Database 
     Dim strSQLChange As String 
     Dim strSQLRestore As String 
     Dim qdfChange As QueryDef 
     Dim rstEmployees As Recordset 
     Dim errLoop As Error 
     
     ' Define two SQL statements for action queries. 
     strSQLChange = "UPDATE Employees SET Country = " & _ 
     "'United States' WHERE Country = 'USA'" 
     strSQLRestore = "UPDATE Employees SET Country = " & _ 
     "'USA' WHERE Country = 'United States'" 
     
     Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
     ' Create temporary QueryDef object. 
     Set qdfChange = dbsNorthwind.CreateQueryDef("", _ 
     strSQLChange) 
     Set rstEmployees = dbsNorthwind.OpenRecordset( _ 
     "SELECT LastName, Country FROM Employees", _ 
     dbOpenForwardOnly) 
     
     ' Print report of original data. 
     Debug.Print _ 
     "Data in Employees table before executing the query" 
     PrintOutput rstEmployees 
     
     ' Run temporary QueryDef. 
     ExecuteQueryDef qdfChange, rstEmployees 
     
     ' Print report of new data. 
     Debug.Print _ 
     "Data in Employees table after executing the query" 
     PrintOutput rstEmployees 
     
     ' Run action query to restore data. Trap for errors, 
     ' checking the Errors collection if necessary. 
     On Error GoTo Err_Execute 
     dbsNorthwind.Execute strSQLRestore, dbFailOnError 
     On Error GoTo 0 
     
     ' Retrieve the current data by requerying the recordset. 
     rstEmployees.Requery 
     
     ' Print report of restored data. 
     Debug.Print "Data after executing the query " & _ 
     "to restore the original information" 
     PrintOutput rstEmployees 
     
     rstEmployees.Close 
     
     Exit Sub 
     
    Err_Execute: 
     
     ' Notify user of any errors that result from 
     ' executing the query. 
     If DBEngine.Errors.Count > 0 Then 
     For Each errLoop In DBEngine.Errors 
     MsgBox "Error number: " & errLoop.Number & vbCr & _ 
     errLoop.Description 
     Next errLoop 
     End If 
     
     Resume Next 
     
    End Sub 
     
    Sub ExecuteQueryDef(qdfTemp As QueryDef, _ 
     rstTemp As Recordset) 
     
     Dim errLoop As Error 
     
     ' Run the specified QueryDef object. Trap for errors, 
     ' checking the Errors collection if necessary. 
     On Error GoTo Err_Execute 
     qdfTemp.Execute dbFailOnError 
     On Error GoTo 0 
     
     ' Retrieve the current data by requerying the recordset. 
     rstTemp.Requery 
     
     Exit Sub 
     
    Err_Execute: 
     
     ' Notify user of any errors that result from 
     ' executing the query. 
     If DBEngine.Errors.Count > 0 Then 
     For Each errLoop In DBEngine.Errors 
     MsgBox "Error number: " & errLoop.Number & vbCr & _ 
     errLoop.Description 
     Next errLoop 
     End If 
     
     Resume Next 
     
    End Sub 
     
    Sub PrintOutput(rstTemp As Recordset) 
     
     ' Enumerate Recordset. 
     Do While Not rstTemp.EOF 
     Debug.Print " " & rstTemp!LastName & _ 
     ", " & rstTemp!Country 
     rstTemp.MoveNext 
     Loop 
     
    End Sub
```
