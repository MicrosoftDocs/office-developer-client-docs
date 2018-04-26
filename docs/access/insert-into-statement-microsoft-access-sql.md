---
title: "INSERT INTO Statement (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277575
  
localization_priority: Normal
ms.assetid: d3e44258-79f2-caba-8629-bde03f898f2d
description: "Adds a record or multiple records to a table. This is referred to as an append query."
---

# INSERT INTO Statement (Microsoft Access SQL)

Adds a record or multiple records to a table. This is referred to as an append query.
  
## Syntax

Multiple-record append query:
  
INSERT INTO  *target*  [(  *field1*  [,  *field2*  [, …]])] [IN  *externaldatabase*  ] SELECT [  *source*  .]  *field1*  [,  *field2*  [, …] FROM  *tableexpression* 
  
Single-record append query:
  
INSERT INTO  *target*  [(  *field1*  [,  *field2*  [, …]])] VALUES (  *value1*  [,  *value2*  [, …]) 
  
The INSERT INTO statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *target*  <br/> |The name of the table or query to append records to.  <br/> |
| *field1*  ,  *field2*  <br/> |Names of the fields to append data to, if following a  *target*  argument, or the names of fields to obtain data from, if following a  *source*  argument.  <br/> |
| *externaldatabase*  <br/> |The path to an external database. For a description of the path, see the [IN](http://msdn.microsoft.com/library/5bca25c0-cd00-140f-79b8-80cd2d0c190b%28Office.15%29.aspx) clause.  <br/> |
| *source*  <br/> |The name of the table or query to copy records from.  <br/> |
| *tableexpression*  <br/> |The name of the table or tables from which records are inserted. This argument can be a single table name or a compound resulting from an [INNER JOIN](inner-join-operation-microsoft-access-sql.md), [LEFT JOIN](left-join-right-join-operations-microsoft-access-sql.md), or [RIGHT JOIN](left-join-right-join-operations-microsoft-access-sql.md) operation or a saved query.  <br/> |
| *value1*  ,  *value2*  <br/> |The values to insert into the specific fields of the new record. Each value is inserted into the field that corresponds to the value's position in the list:  *value1*  is inserted into  *field1*  of the new record,  *value2*  into  *field2*  , and so on. You must separate values with a comma, and enclose text fields in quotation marks (' ').  <br/> |
   
## Remarks

You can use the INSERT INTO statement to add a single record to a table using the single-record append query syntax as shown above. In this case, your code specifies the name and value for each field of the record. You must specify each of the fields of the record that a value is to be assigned to and a value for that field. When you do not specify each field, the default value or **Null** is inserted for missing columns. Records are added to the end of the table. 
  
You can also use INSERT INTO to append a set of records from another table or query by using the SELECT … FROM clause as shown above in the multiple-record append query syntax. In this case, the SELECT clause specifies the fields to append to the specified  *target*  table. 
  
The  *source*  or  *target*  table may specify a table or a query. If a query is specified, the Microsoft Access database engine appends records to any and all tables specified by the query. 
  
INSERT INTO is optional but when included, precedes the [SELECT](select-statement-microsoft-access-sql.md) statement. 
  
If your destination table contains a primary key, make sure you append unique, non- **Null** values to the primary key field or fields; if you do not, the Microsoft Access database engine will not append the records. 
  
If you append records to a table with an AutoNumber field and you want to renumber the appended records, do not include the AutoNumber field in your query. Do include the AutoNumber field in the query if you want to retain the original values from the field.
  
Use the IN clause to append records to a table in another database.
  
To create a new table, use the [SELECT… INTO](select-into-statement-microsoft-access-sql.md) statement instead to create a make-table query. 
  
To find out which records will be appended before you run the append query, first execute and view the results of a select query that uses the same selection criteria.
  
An append query copies records from one or more tables to another. The tables that contain the records you append are not affected by the append query.
  
Instead of appending existing records from another table, you can specify the value for each field in a single new record using the VALUES clause. If you omit the field list, the VALUES clause must include a value for every field in the table; otherwise, the INSERT operation will fail. Use an additional INSERT INTO statement with a VALUES clause for each additional record you want to create.
  
 **Links provided by:**![Community Member Icon](media/8b9774c4-6c97-470e-b3a2-56d8f786444c.png) The [UtterAccess](http://www.utteraccess.com) community | [About the Contributors](#AboutContributors)
  
- [Generating sequential numbers for INSERT/UPDATE statements](http://www.utteraccess.com/forum/Generating-sequential-num-t446039.mdl)
    
- [SQL to VBA Formatter](http://www.utteraccess.com/forum/SQL-VBA-Formatter-t1165308.mdl)
    
## Example

This example selects all records in a hypothetical New Customers table and adds them to the Customers table. When individual columns are not designated, the SELECT table column names must match exactly those in the INSERT INTO table.
  
```
Sub InsertIntoX1() 
 
    Dim dbs As Database 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    ' Select all records in the New Customers table  
    ' and add them to the Customers table. 
    dbs.Execute " INSERT INTO Customers " _ 
        &amp; "SELECT * " _ 
        &amp; "FROM [New Customers];" 
         
    dbs.Close 
 
End Sub
```

This example creates a new record in the Employees table.
  
```
Sub InsertIntoX2() 
 
    Dim dbs As Database 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    ' Create a new record in the Employees table. The  
    ' first name is Harry, the last name is Washington,  
    ' and the job title is Trainee. 
    dbs.Execute " INSERT INTO Employees " _ 
        &amp; "(FirstName,LastName, Title) VALUES " _ 
        &amp; "('Harry', 'Washington', 'Trainee');" 
         
    dbs.Close 
 
End Sub 

```

## About the Contributors
<a name="AboutContributors"> </a>

UtterAccess is the premier Microsoft Access wiki and help forum. Click here to join. 
  

