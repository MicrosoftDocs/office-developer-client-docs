---
title: "CREATE PROCEDURE Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 1fbb5267-9862-bfb4-6436-176152d7a6cd
description: "Creates a stored procedure."
---

# CREATE PROCEDURE Statement (Microsoft Access SQL)

Creates a stored procedure.
  
> [!NOTE]
> The Microsoft Access database engine does not support the use of CREATE PROCEDURE, or any of the DDL statements, with non-Microsoft Jet database engine databases. 
  
## Syntax

CREATE PROCEDURE  *procedure*  [  *param1 datatype*  [,  *param2 datatype*  [, …]] AS sqlstatement 
  
The CREATE PROCEDURE statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *procedure*  <br/> |A name for the procedure. It must follow standard naming conventions.  <br/> |
| *param1*  ,  *param2*  <br/> |From one to 255 field names or parameters. For example:  <br/> ```CREATE PROCEDURE Sales_By_Country [Beginning Date] DateTime, [Ending Date] DateTime;```For more information on parameters, see [PARAMETERS](parameters-declaration-microsoft-access-sql.md).  <br/> |
| *datatype*  <br/> |One of the primary [Microsoft Access SQL data types](sql-data-types.md) or their synonyms.  <br/> |
| *sqlstatement*  <br/> |An SQL statement such as SELECT, UPDATE, DELETE, INSERT, CREATE TABLE, DROP TABLE, and so on.  <br/> |
   
## Remarks

An SQL procedure consists of a PROCEDURE clause that specifies the name of the procedure, an optional list of parameter definitions, and a single SQL statement.
  
A procedure name cannot be the same as the name of an existing table.
  
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
    EnumFields rst, 15 
     
    ' Delete the QueryDef because this is a 
    ' demonstration. 
    dbs.QueryDefs.Delete "NewQry" 
     
    dbs.Close 
 
End Sub 

```

