---
title: "Database.QueryTimeout Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: c83ca852-715a-c853-429b-80a15c3fc39b
description: "Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source."
---

# Database.QueryTimeout Property (DAO)

Sets or returns a value that specifies the number of seconds to wait before a timeout error occurs when a query is executed on an ODBC data source.
  
## Syntax

 *expression*  . **QueryTimeout**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

The default value is 60.
  
When you're using an ODBC database, such as Microsoft SQL Server, there may be delays due to network traffic or heavy use of the ODBC server. Rather than waiting indefinitely, you can specify how long to wait.
  
When you use **QueryTimeout** with a **[Connection](connection-object-dao.md)** or **[Database](database-object-dao.md)** object, it specifies a global value for all queries associated with the database. You can override this value for a specific query by setting the **ODBCTimeout** property of the particular **[QueryDef](querydef-object-dao.md)** object. 
  
## Example

This example uses the **ODBCTimeout** and **QueryTimeout** properties to show how the **QueryTimeout** setting on a **Database** object sets the default **ODBCTimeout** setting on any **QueryDef** objects created from the **Database** object. 
  
```
Sub ODBCTimeoutX() 
 
 Dim dbsCurrent As Database 
 Dim qdfStores As QueryDef 
 Dim rstStores As Recordset 
 
 Set dbsCurrent = OpenDatabase("Northwind.mdb") 
 
 ' Change the default QueryTimeout of the Northwind 
 ' database. 
 Debug.Print "Default QueryTimeout of Database: " &amp; _ 
 dbsCurrent.QueryTimeout 
 dbsCurrent.QueryTimeout = 30 
 Debug.Print "New QueryTimeout of Database: " &amp; _ 
 dbsCurrent.QueryTimeout 
 
 ' Create a new QueryDef object. 
 Set qdfStores = dbsCurrent.CreateQueryDef("Stores", _ 
 "SELECT * FROM stores") 
 
 ' Note: The DSN referenced below must be configured to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the SQL Server. 
 qdfStores.Connect = _ 
 "ODBC;DATABASE=pubs;DSN=Publishers" 
 
 ' Change the ODBCTimeout setting of the new QueryDef 
 ' object from its default setting. 
 Debug.Print "Default ODBCTimeout of QueryDef: " &amp; _ 
 qdfStores.ODBCTimeout 
 qdfStores.ODBCTimeout = 0 
 Debug.Print "New ODBCTimeout of QueryDef: " &amp; _ 
 qdfStores.ODBCTimeout 
 
 ' Execute the query and display the results. 
 Set rstStores = qdfStores.OpenRecordset() 
 
 Debug.Print "Contents of recordset:" 
 With rstStores 
 Do While Not .EOF 
 Debug.Print , .Fields(0), .Fields(1) 
 .MoveNext 
 Loop 
 .Close 
 End With 
 
 ' Delete new QueryDef because this is a demonstration. 
 dbsCurrent.QueryDefs.Delete qdfStores.Name 
 dbsCurrent.Close 
 
End Sub 
 
```


