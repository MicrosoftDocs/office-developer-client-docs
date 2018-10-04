---
title: QueryDef.MaxRecords Property (DAO)
TOCTitle: MaxRecords Property
ms:assetid: 7492cde9-be30-3473-dabc-9602465910d1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff195877(v=office.15)
ms:contentKeyID: 48545664
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053583
f1_categories:
- Office.Version=v15
---

# QueryDef.MaxRecords Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Sets or returns the maximum number of records to return from a query against an ODBC data source.

## Syntax

*expression* .MaxRecords

*expression* A variable that represents a **QueryDef** object.

## Remarks

The default value is 0, indicating no limit on the number of records returned.

Once the number of rows specified by **MaxRecords** is returned to your application in a **[Recordset](recordset-object-dao.md)**, the query processor will stop returning additional records even if more records would qualify for inclusion in the **Recordset**. This property is useful in situations where limited client resources prohibit management of large numbers of records.


> [!NOTE]
> <P>The <STRONG>MaxRecords</STRONG> property can only be used with an ODBC data source.</P>



## Example

This example uses the **MaxRecords** property to set a limit on how many records are returned by a query on an ODBC data source.

``` 
Sub MaxRecordsX() 
 
 Dim dbsCurrent As Database 
 Dim qdfPassThrough As QueryDef 
 Dim qdfLocal As QueryDef 
 Dim rstTemp As Recordset 
 
 ' Open a database from which QueryDef objects can be 
 ' created. 
 Set dbsCurrent = OpenDatabase("DB1.mdb") 
 
 ' Create a pass-through query to retrieve data from 
 ' a Microsoft SQL Server database. 
 Set qdfPassThrough = _ 
 dbsCurrent.CreateQueryDef("") 
 
 ' Set the properties of the new query, limiting the 
 ' number of returnable records to 20. 
 ' Note: The DSN referenced below must be configured to 
 ' use Microsoft Windows NT Authentication Mode to 
 ' authorize user access to the Microsoft SQL Server. 
 qdfPassThrough.Connect = _ 
 "ODBC;DATABASE=pubs;DSN=Publishers" 
 qdfPassThrough.SQL = "SELECT * FROM titles" 
 qdfPassThrough.ReturnsRecords = True 
 qdfPassThrough.MaxRecords = 20 
 
 Set rstTemp = qdfPassThrough.OpenRecordset() 
 
 ' Display results of query. 
 Debug.Print "Query results:" 
 With rstTemp 
 Do While Not .EOF 
 Debug.Print , .Fields(0), .Fields(1) 
 .MoveNext 
 Loop 
 .Close 
 End With 
 
 dbsCurrent.Close 
 
End Sub 
 
```

