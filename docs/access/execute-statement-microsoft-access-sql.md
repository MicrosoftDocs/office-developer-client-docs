---
title: "EXECUTE Statement (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 9/28/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277471
  
localization_priority: Normal
ms.assetid: 9ec4d9ee-db2a-0319-3ccf-c035d67a1496
description: "Used to invoke the execution of a procedure."
---

# EXECUTE Statement (Microsoft Access SQL)

Used to invoke the execution of a procedure.
  
## Syntax

EXECUTE  *procedure*  [  *param1*  [,  *param2*  [, …]] 
  
The EXECUTE statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *procedure*  <br/> |The name of the procedure that is to be executed.  <br/> |
| *param1, param2, …*  <br/> |Values for the parameters defined by the procedure.  <br/> |
   
## Example

This example names the query CategoryList.
  
This example calls the EnumFields procedure, which you can find in the SELECT statement example.
  
```
Sub ProcedureX() 
 
    Dim dbs As Database, rst As Recordset 
    Dim qdf As QueryDef, strSql As String 
     
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    strSql = "PROCEDURE CategoryList; " _ 
        &amp; "SELECT DISTINCTROW CategoryName, " _ 
        &amp; "CategoryID FROM Categories " _ 
        &amp; "ORDER BY CategoryName;" 
     
    ' Create a named QueryDef based on the SQL 
    ' statement. 
    Set qdf = dbs.CreateQueryDef("NewQry", strSql) 
 
    ' Create a temporary snapshot-type Recordset. 
    Set rst = qdf.OpenRecordset(dbOpenSnapshot) 
 
    ' Populate the Recordset. 
    rst.MoveLast 
             
    ' Call EnumFields to print the contents of the  
    ' Recordset. Pass the Recordset object and desired 
    ' field width. 
    Execute EnumFields rst, 15 
     
    ' Delete the QueryDef because this is a 
    ' demonstration. 
    dbs.QueryDefs.Delete "NewQry" 
     
    dbs.Close 
 
End Sub
```


