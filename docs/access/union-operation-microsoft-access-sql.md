---
title: "UNION Operation (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277582
  
localization_priority: Normal
ms.assetid: a5139921-51e5-7d96-74e3-11c3fd5f7eaa
description: "Creates a union query, which combines the results of two or more independent queries or tables."
---

# UNION Operation (Microsoft Access SQL)

Creates a union query, which combines the results of two or more independent queries or tables.
  
## Syntax

[TABLE]  *query1*  UNION [ALL] [TABLE]  *query2*  [UNION [ALL] [TABLE]  *queryn*  [ … ]] 
  
The UNION operation has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *query1-n*  <br/> |A SELECT statement, the name of a stored query, or the name of a stored table preceded by the TABLE keyword.  <br/> |
   
## Remarks

You can merge the results of two or more queries, tables, and SELECT statements, in any combination, in a single UNION operation. The following example merges an existing table named New Accounts and a SELECT statement:
  
```
TABLE [New Accounts] UNION ALL 
SELECT * 
FROM Customers 
WHERE OrderAmount > 1000;
```

By default, no duplicate records are returned when you use a UNION operation; however, you can include the [ALL](http://msdn.microsoft.com/library/6ff5c418-897b-7d65-8551-5a0ace3c587f%28Office.15%29.aspx) predicate to ensure that all records are returned. This also makes the query run faster. 
  
All queries in a UNION operation must request the same number of fields; however, the fields do not have to be of the same size or data type.
  
Use aliases only in the first SELECT statement because they are ignored in any others. In the ORDER BY clause, refer to fields by what they are called in the first SELECT statement.
  
> [!NOTE]
>  You can use a [GROUP BY](http://msdn.microsoft.com/library/fe7d5e27-a47a-1229-232c-cf6a0cbad761%28Office.15%29.aspx) or [HAVING](http://msdn.microsoft.com/library/4fc4655b-c8a6-2ca2-509e-ac98d9a1c776%28Office.15%29.aspx) clause in each  *query*  argument to group the returned data. >  You can use an [ORDER BY](http://msdn.microsoft.com/library/9e5e6911-1117-b220-7f11-1ae7f87cbdc0%28Office.15%29.aspx) clause at the end of the last  *query*  argument to display the returned data in a specified order. 
  
## Example

This example retrieves the names and cities of all suppliers and customers in Brazil.
  
This example calls the EnumFields procedure, which you can find in the SELECT statement example.
  
```
Sub UnionX() 
 
    Dim dbs As Database, rst As Recordset 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    ' Retrieve the names and cities of all suppliers  
    ' and customers in Brazil. 
    Set rst = dbs.OpenRecordset("SELECT CompanyName," _ 
        &amp; " City FROM Suppliers" _ 
        &amp; " WHERE Country = 'Brazil' UNION" _ 
        &amp; " SELECT CompanyName, City FROM Customers" _ 
        &amp; " WHERE Country = 'Brazil';") 
     
    ' Populate the Recordset. 
    rst.MoveLast 
     
    ' Call EnumFields to print the contents of the  
    ' Recordset. Pass the Recordset object and desired 
    ' field width. 
    EnumFields rst, 12 
 
    dbs.Close 
 
End Sub
```


