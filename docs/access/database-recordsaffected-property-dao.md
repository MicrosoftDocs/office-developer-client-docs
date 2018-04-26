---
title: "Database.RecordsAffected Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 1c591231-21dd-f0b1-4ba6-87784c5890d3
description: "Returns the number of records affected by the most recently invoked Execute method."
---

# Database.RecordsAffected Property (DAO)

Returns the number of records affected by the most recently invoked **[Execute](connection-execute-method-dao.md)** method. 
  
## Syntax

 *expression*  . **RecordsAffected**
  
 *expression*  A variable that represents a **Database** object. 
  
## Example

This example uses the **RecordsAffected** property with action queries executed from a **Database** object and from a **QueryDef** object. The RecordsAffectedOutput function is required for this procedure to run. 
  
```
Sub RecordsAffectedX() 
 
 Dim dbsNorthwind As Database 
 Dim qdfTemp As QueryDef 
 Dim strSQLChange As String 
 Dim strSQLRestore As String 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 With dbsNorthwind 
 ' Print report of contents of the Employees 
 ' table. 
 Debug.Print _ 
 "Number of records in Employees table: " &amp; _ 
 .TableDefs!Employees.RecordCount 
 RecordsAffectedOutput dbsNorthwind 
 
 ' Define and execute an action query. 
 strSQLChange = "UPDATE Employees " &amp; _ 
 "SET Country = 'United States' " &amp; _ 
 "WHERE Country = 'USA'" 
 .Execute strSQLChange 
 
 ' Print report of contents of the Employees 
 ' table. 
 Debug.Print _ 
 "RecordsAffected after executing query " &amp; _ 
 "from Database: " &amp; .RecordsAffected 
 RecordsAffectedOutput dbsNorthwind 
 
 ' Define and run another action query. 
 strSQLRestore = "UPDATE Employees " &amp; _ 
 "SET Country = 'USA' " &amp; _ 
 "WHERE Country = 'United States'" 
 Set qdfTemp = .CreateQueryDef("", strSQLRestore) 
 qdfTemp.Execute 
 
 ' Print report of contents of the Employees 
 ' table. 
 Debug.Print _ 
 "RecordsAffected after executing query " &amp; _ 
 "from QueryDef: " &amp; qdfTemp.RecordsAffected 
 RecordsAffectedOutput dbsNorthwind 
 
 .Close 
 
 End With 
 
End Sub 
 
Function RecordsAffectedOutput(dbsNorthwind As Database) 
 
 Dim rstEmployees As Recordset 
 
 ' Open a Recordset object from the Employees table. 
 Set rstEmployees = _ 
 dbsNorthwind.OpenRecordset("Employees") 
 
 With rstEmployees 
 ' Enumerate Recordset. 
 .MoveFirst 
 Do While Not .EOF 
 Debug.Print " " &amp; !LastName &amp; ", " &amp; !Country 
 .MoveNext 
 Loop 
 .Close 
 End With 
 
End Function 

```


