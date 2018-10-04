---
title: QueryDef.Prepare Property (DAO)
TOCTitle: Prepare Property
ms:assetid: d5a285c4-bd00-028b-b785-f1890db29bab
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff835035(v=office.15)
ms:contentKeyID: 48547968
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1101187
f1_categories:
- Office.Version=v15
---

# QueryDef.Prepare Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

## Syntax

*expression* .Prepare

*expression* A variable that represents a **QueryDef** object.

## Remarks

You can use the **Prepare** property to either have the server create a temporary stored procedure from your query and then execute it, or just have the query executed directly. By default the **Prepare** property is set to **dbQPrepare**. However, you can set this property to **dbQUnprepare** to prohibit preparing of the query. In this case, the query is executed using the **SQLExecDirect** API.

Creating a stored procedure can slow down the initial operation, but increases performance of all subsequent references to the query. However, some queries cannot be executed in the form of stored procedures. In these cases, you must set the **Prepare** property to **dbQUnprepare**.

If **Prepare** is set to **dbQPrepare**, this can be overridden when the query is executed by setting the **[Execute](querydef-execute-method-dao.md)** method's options argument to **dbExecDirect**.


> [!NOTE]
> <P>The ODBC <STRONG>SQLPrepare</STRONG> API is called as soon as the DAO <STRONG><A href="querydef-sql-property-dao.md">SQL</A></STRONG> property is set. Therefore, if you want to improve performance using the <STRONG>dbQUnprepare</STRONG> option, you must set the <STRONG>Prepare</STRONG> property before setting the <STRONG>SQL</STRONG> property.</P>



## Example

This example uses the **Prepare** property to specify that a query should be executed directly rather than first creating a temporary stored procedure on the server.

``` 
Sub PrepareX() 
 
 Dim wrkODBC As Workspace 
 Dim conPubs As Connection 
 Dim qdfTemp As QueryDef 
 Dim rstTemp As Recordset 
 
 ' Create ODBCDirect Workspace object and open Connection 
 ' object. 
 Set wrkODBC = CreateWorkspace("", _ 
 "admin", "", dbUseODBC) 
 
 ' Note: The DSN referenced below must be configured to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 Set conPubs = wrkODBC.OpenConnection("Publishers", , , _ 
 "ODBC;DATABASE=pubs;DSN=Publishers") 
 
 Set qdfTemp = conPubs.CreateQueryDef("") 
 
 With qdfTemp 
 ' Because you will only run this query once, specify 
 ' the ODBC SQLExecDirect API function. If you do 
 ' not set this property before you set the SQL 
 ' property, the ODBC SQLPrepare API function will 
 ' be called anyway which will nullify any 
 ' performance gain. 
 .Prepare = dbQUnprepare 
 .SQL = "UPDATE roysched " & _ 
 "SET royalty = royalty * 2 " & _ 
 "WHERE title_id LIKE 'BU____' OR " & _ 
 "title_id LIKE 'PC____'" 
 .Execute 
 End With 
 
 Debug.Print "Query results:" 
 
 ' Open recordset containing modified records. 
 Set rstTemp = conPubs.OpenRecordset( _ 
 "SELECT * FROM roysched " & _ 
 "WHERE title_id LIKE 'BU____' OR " & _ 
 "title_id LIKE 'PC____'") 
 
 ' Enumerate recordset. 
 With rstTemp 
 Do While Not .EOF 
 Debug.Print , !title_id, !lorange, _ 
 !hirange, !royalty 
 .MoveNext 
 Loop 
 .Close 
 End With 
 
 conPubs.Close 
 wrkODBC.Close 
 
```

