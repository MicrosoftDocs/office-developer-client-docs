---
title: "PARAMETERS Declaration (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277577
  
localization_priority: Normal
ms.assetid: 0dcaad68-6a5f-93dc-e62a-b82b36e1e69c
description: "Declares the name and data type of each parameter in a parameter query."
---

# PARAMETERS Declaration (Microsoft Access SQL)

Declares the name and data type of each parameter in a parameter query.
  
## Syntax

PARAMETERS  *name datatype*  [,  *name datatype*  [, …]] 
  
The PARAMETERS declaration has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *name*  <br/> |The name of the parameter. Assigned to the **Name** property of the **Parameter** object and used to identify this parameter in the **Parameters** collection. You can use  *name*  as a string that is displayed in a dialog box while your application runs the query. Use brackets ([ ]) to enclose text that contains spaces or punctuation. For example, [Low price] and [Begin report with which month?] are valid  *name*  arguments.  <br/> |
| *datatype*  <br/> |One of the primary [Microsoft Access SQL data types](sql-data-types.md) or their synonyms.  <br/> |
   
## Remarks

For queries that you run regularly, you can use a PARAMETERS declaration to create a parameter query. A parameter query can help automate the process of changing query criteria. With a parameter query, your code will need to provide the parameters each time the query is run.
  
The PARAMETERS declaration is optional but when included precedes any other statement, including [SELECT](select-statement-microsoft-access-sql.md).
  
If the declaration includes more than one parameter, separate them with commas. The following example includes two parameters:
  
```
PARAMETERS [Low price] Currency, [Beginning date] DateTime;
```

You can use  *name*  but not  *datatype*  in a [WHERE](http://msdn.microsoft.com/library/67e4caed-6512-e8bd-39d0-6dca18114b18%28Office.15%29.aspx) or [HAVING](http://msdn.microsoft.com/library/4fc4655b-c8a6-2ca2-509e-ac98d9a1c776%28Office.15%29.aspx) clause. The following example expects two parameters to be provided and then applies the criteria to records in the Orders table: 
  
```
PARAMETERS [Low price] Currency, 
[Beginning date] DateTime; 
SELECT OrderID, OrderAmount
FROM Orders 
WHERE OrderAmount > [Low price] 
AND OrderDate >= [Beginning date];
```

## Example

This example requires the user to provide a job title and then uses that job title as the criteria for the query.
  
This example calls the EnumFields procedure, which you can find in the [SELECT statement](select-statement-microsoft-access-sql.md) example. 
  
```
Sub ParametersX() 
 
    Dim dbs As Database, qdf As QueryDef 
    Dim rst As Recordset 
    Dim strSql As String, strParm As String 
    Dim strMessage As String 
    Dim intCommand As Integer 
     
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("NorthWind.mdb") 
     
    ' Define the parameters clause. 
    strParm = "PARAMETERS [Employee Title] CHAR; " 
 
    ' Define an SQL statement with the parameters 
    ' clause. 
    strSql = strParm &amp; "SELECT LastName, FirstName, " _ 
        &amp; "EmployeeID " _ 
        &amp; "FROM Employees " _ 
        &amp; "WHERE Title =[Employee Title];" 
     
    ' Create a QueryDef object based on the  
    ' SQL statement. 
    Set qdf = dbs.CreateQueryDef _ 
        ("Find Employees", strSql) 
     
    Do While True 
        strMessage = "Find Employees by Job " _ 
            &amp; "title:" &amp; Chr(13) _ 
            &amp; "  Choose Job Title:" &amp; Chr(13) _ 
            &amp; "   1 - Sales Manager" &amp; Chr(13) _ 
            &amp; "   2 - Sales Representative" &amp; Chr(13) _ 
            &amp; "   3 - Inside Sales Coordinator" 
         
        intCommand = Val(InputBox(strMessage)) 
         
        Select Case intCommand 
            Case 1 
                qdf("Employee Title") = _ 
                    "Sales Manager" 
            Case 2 
                qdf("Employee Title") = _ 
                    "Sales Representative" 
            Case 3 
                qdf("Employee Title") = _ 
                    "Inside Sales Coordinator" 
            Case Else 
                Exit Do 
        End Select 
         
        ' Create a temporary snapshot-type Recordset. 
        Set rst = qdf.OpenRecordset(dbOpenSnapshot) 
 
        ' Populate the Recordset. 
        rst.MoveLast 
             
        ' Call EnumFields to print the contents of the  
        ' Recordset. Pass the Recordset object and desired 
        ' field width. 
        EnumFields rst, 12 
 
    Loop 
     
    ' Delete the QueryDef because this is a 
    ' demonstration. 
    dbs.QueryDefs.Delete "Find Employees" 
     
    dbs.Close 
 
End Sub
```


