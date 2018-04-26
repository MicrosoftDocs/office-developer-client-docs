---
title: "PROCEDURE Clause (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277578
  
localization_priority: Normal
ms.assetid: a718802c-9260-88d5-ec29-d5e5594927b0

description: "Defines a name and optional parameters for a query."
---

# PROCEDURE Clause (Microsoft Access SQL)

Defines a name and optional parameters for a query.
  
> [!NOTE]
> The PROCEDURE clause has been superseded by the PROCEDURE statement. Although the PROCEDURE clause is still supported, the PROCEDURE statement provides a superset of the capability of the PROCEDURE clause and is the recommended syntax. 
  
## Syntax

PROCEDURE  *name*  [  *param1 datatype*  [,  *param2 datatype*  [, …]] 
  
The PROCEDURE clause has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *name*  <br/> |A name for the procedure. It must follow standard naming conventions.  <br/> |
| *param1*  ,  *param2*  <br/> |One or more field names or parameters. For example:  <br/> ```PROCEDURE Sales_By_Country [Beginning Date] DateTime, [Ending Date] DateTime;```For more information on parameters, see [parameters](parameters-declaration-microsoft-access-sql.md).  <br/> |
| *datatype*  <br/> |One of the primary [Microsoft Access SQL data types](sql-data-types.md) or their synonyms.  <br/> |
   
## Remarks

An SQL procedure consists of a PROCEDURE clause (which specifies the name of the procedure), an optional list of parameter definitions, and a single SQL statement. For example, the procedure Get_Part_Number might run a query that retrieves a specified part number.
  
> [!NOTE]
>  If the clause includes more than one field definition (that is,  *param-datatype*  pairs), separate them with commas. >  The PROCEDURE clause must be followed by an SQL statement (for example, a [SELECT](select-statement-microsoft-access-sql.md) or [UPDATE](update-statement-microsoft-access-sql.md) statement). 
  
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

