---
title: QueryDef.ODBCTimeout Property (DAO)
TOCTitle: ODBCTimeout Property
ms:assetid: b251c4fb-64a8-aa95-deed-64425df3e00c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff822019(v=office.15)
ms:contentKeyID: 48547166
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053052
f1_categories:
- Office.Version=v15
---

# QueryDef.ODBCTimeout Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Indicates the number of seconds to wait before a timeout error occurs when a **[QueryDef](querydef-object-dao.md)** is executed on an ODBC database.

## Syntax

*expression* .ODBCTimeout

*expression* A variable that represents a **QueryDef** object.

## Remarks

When the **ODBCTimeout** property is set to -1, the timeout defaults to the current setting of the **[QueryTimeout](database-querytimeout-property-dao.md)** property of the **[Connection](connection-object-dao.md)** or **[Database](database-object-dao.md)** object that contains the **QueryDef**. When the **ODBCTimeout** property is set to 0, no timeout error occurs.

When you're using an ODBC database, such as Microsoft SQL Server, delays can occur because of network traffic or heavy use of the ODBC server. Rather than waiting indefinitely, you can specify how long to wait before returning an error.

Setting the **ODBCTimeout** property of a **QueryDef** object overrides the value specified by the **QueryTimeout** property of the **Connection** or **Database** object containing the **QueryDef**, but only for that **QueryDef** object.

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
 Debug.Print "Default QueryTimeout of Database: " & _ 
 dbsCurrent.QueryTimeout 
 dbsCurrent.QueryTimeout = 30 
 Debug.Print "New QueryTimeout of Database: " & _ 
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
 Debug.Print "Default ODBCTimeout of QueryDef: " & _ 
 qdfStores.ODBCTimeout 
 qdfStores.ODBCTimeout = 0 
 Debug.Print "New ODBCTimeout of QueryDef: " & _ 
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

