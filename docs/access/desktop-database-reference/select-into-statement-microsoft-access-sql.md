---
title: SELECT.INTO statement (Microsoft Access SQL)
TOCTitle: SELECT.INTO statement (Microsoft Access SQL)
ms:assetid: 29f3bd55-52f5-a36e-4e33-4b3499c6ce8d
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192059(v=office.15)
ms:contentKeyID: 48543897
ms.date: 03/22/2022
mtps_version: v=office.15
ms.localizationpriority: high
---

# SELECT.INTO statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Creates a make-table query.

## Syntax

SELECT *field1*\[, *field2*\[, …\]\] INTO *newtable* \[IN *externaldatabase*\] FROM *source*

The SELECT…INTO statement has these parts:

|**Part**|**Description**|
|:-------|:--------------|
| _field1,field2_ | The name of the fields to be copied into the new table.</br>|
| _newtable_ | The name of the table to be created. It must conform to standard naming conventions. If <em>newtable</em> is the same as the name of an existing table, a trappable error occurs.</p></td>
| _externaldatabase_ | The path to an external database. For a description of the path, see the [IN](/office/vba/access/concepts/miscellaneous/in-clause-microsoft-access-sql.md) clause.</br>|
| _source_ | The name of the existing table from which records are selected. This can be single or multiple tables or a query.</br>|

## Remarks

You can use make-table queries to archive records, make backup copies of your tables, or make copies to export to another database or to use as a basis for reports that display data for a particular time period. For example, you could produce a Monthly Sales by Region report by running the same make-table query each month.

> [!NOTE]
>
> - You may want to define a primary key for the new table. When you create the table, the fields in the new table inherit the data type and field size of each field in the query's underlying tables, but no other field or table properties are transferred.
> - To add data to an existing table, use the [INSERT INTO](insert-into-statement-microsoft-access-sql.md) statement instead to create an append query.
> - To find out which records will be selected before you run the make-table query, first examine the results of a [SELECT](select-statement-microsoft-access-sql.md) statement that uses the same selection criteria.

## Example

This example selects all records in the Employees table and copies them into a new table named Emp Backup.

```vb
    Sub SelectIntoX() 
     
        Dim dbs As Database 
        Dim qdf As QueryDef 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
     
        ' Select all records in the Employees table  
        ' and copy them into a new table, Emp Backup. 
        dbs.Execute "SELECT Employees.* INTO " _ 
            & "[Emp Backup] FROM Employees;" 
             
        ' Delete the table because this is a demonstration. 
        dbs.Execute "DROP TABLE [Emp Backup];" 
         
        dbs.Close 
     
    End Sub
```
