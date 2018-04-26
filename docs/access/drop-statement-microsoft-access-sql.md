---
title: "DROP Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a8c79c35-22da-2e6d-88b5-620eb481bb61
description: "Deletes an existing table, procedure, or view from a database, or deletes an existing index from a table."
---

# DROP Statement (Microsoft Access SQL)

Deletes an existing table, procedure, or view from a database, or deletes an existing index from a table.
  
> [!NOTE]
> The Microsoft Access database engine does not support the use of DROP, or any of the DDL statements, with non-Microsoft Access database engine databases. Use the DAO **Delete** method instead. 
  
## Syntax

DROP {TABLE  *table*  | INDEX  *index*  ON  *table*  | PROCEDURE  *procedure*  | VIEW  *view*  } 
  
The DROP statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *table*  <br/> |The name of the table to be deleted or the table from which an index is to be deleted.  <br/> |
| *procedure*  <br/> |The name of the procedure to be deleted.  <br/> |
| *view*  <br/> |The name of the view to be deleted.  <br/> |
| *index*  <br/> |The name of the index to be deleted from  *table.*  <br/> |
   
## Remarks

You must close the table before you can delete it or remove an index from it.
  
You can also use [ALTER TABLE](alter-table-statement-microsoft-access-sql.md) to delete an index from a table. 
  
You can use [CREATE TABLE](create-table-statement-microsoft-access-sql.md) to create a table and [CREATE INDEX](create-index-statement-microsoft-access-sql.md) or ALTER TABLE to create an index. To modify a table, use ALTER TABLE. 
  
## Example

The following example assumes the existence of a hypothetical NewIndex index on the Employees table in the Northwind database.
  
This example deletes the index MyIndex from the Employees table.
  
```
Sub DropX1() 
 
    Dim dbs As Database 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
 
    ' Delete NewIndex from the Employees table. 
    dbs.Execute "DROP INDEX NewIndex ON Employees;" 
 
    dbs.Close 
 
End Sub
```

This example deletes the Employees table from the database.
  
```
Sub DropX2() 
 
    Dim dbs As Database 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
 
    ' Delete the Employees table. 
    dbs.Execute "DROP TABLE Employees;" 
 
    dbs.Close 
 
End Sub
```


