---
title: INSERT INTO statement (Microsoft Access SQL)
TOCTitle: INSERT INTO statement (Microsoft Access SQL)
ms:assetid: d3e44258-79f2-caba-8629-bde03f898f2d
ms:mtpsurl: https://msdn.microsoft.com/library/Ff834799(v=office.15)
ms:contentKeyID: 48547918
ms.date: 10/18/2018
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277575
f1_categories:
- Office.Version=v15
ms.localizationpriority: high
---

# INSERT INTO statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Adds a record or multiple records to a table. This is referred to as an append query.

## Syntax

### Multiple-record append query

INSERT INTO *target* \[(*field1*\[, *field2*\[, …\]\])\] \[IN *externaldatabase*\] SELECT \[*source*.\]*field1*\[, *field2*\[, …\] FROM *tableexpression*

### Single-record append query

INSERT INTO *target* \[(*field1*\[, *field2*\[, …\]\])\] VALUES (*value1*\[, *value2*\[, …\])

The INSERT INTO statement has these parts:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>target</em></p></td>
<td><p>The name of the table or query to append records to.</p></td>
</tr>
<tr class="even">
<td><p><em>field1</em>, <em>field2</em></p></td>
<td><p>Names of the fields to append data to, if following a <em>target</em> argument, or the names of fields to obtain data from, if following a <em>source</em> argument.</p></td>
</tr>
<tr class="odd">
<td><p><em>externaldatabase</em></p></td>
<td><p>The path to an external database. For a description of the path, see the <a href="https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/in-clause-microsoft-access-sql">IN</a> clause.</p></td>
</tr>
<tr class="even">
<td><p><em>source</em></p></td>
<td><p>The name of the table or query to copy records from.</p></td>
</tr>
<tr class="odd">
<td><p><em>tableexpression</em></p></td>
<td><p>The name of the table or tables from which records are inserted. This argument can be a single table name or a compound resulting from an <a href="inner-join-operation-microsoft-access-sql.md">INNER JOIN</a>, <a href="left-join-right-join-operations-microsoft-access-sql.md">LEFT JOIN</a>, or <a href="left-join-right-join-operations-microsoft-access-sql.md">RIGHT JOIN</a> operation or a saved query.</p></td>
</tr>
<tr class="even">
<td><p><em>value1</em>, <em>value2</em></p></td>
<td><p>The values to insert into the specific fields of the new record. Each value is inserted into the field that corresponds to the value's position in the list: <em>value1</em> is inserted into <em>field1</em> of the new record, <em>value2</em> into <em>field2</em>, and so on. You must separate values with a comma, and enclose text fields in quotation marks (' ').</p></td>
</tr>
</tbody>
</table>


## Remarks

You can use the INSERT INTO statement to add a single record to a table using the single-record append query syntax as shown above. In this case, your code specifies the name and value for each field of the record. You must specify each of the fields of the record that a value is to be assigned to and a value for that field. When you do not specify each field, the default value or **Null** is inserted for missing columns. Records are added to the end of the table.

You can also use INSERT INTO to append a set of records from another table or query by using the SELECT … FROM clause as shown above in the multiple-record append query syntax. In this case, the SELECT clause specifies the fields to append to the specified *target* table.

The *source* or *target* table may specify a table or a query. If a query is specified, the Microsoft Access database engine appends records to any and all tables specified by the query.

INSERT INTO is optional but when included, precedes the [SELECT](select-statement-microsoft-access-sql.md) statement.

If your destination table contains a primary key, make sure you append unique, non-**Null** values to the primary key field or fields; if you do not, the Microsoft Access database engine will not append the records.

If you append records to a table with an AutoNumber field and you want to renumber the appended records, do not include the AutoNumber field in your query. Do include the AutoNumber field in the query if you want to retain the original values from the field.

Use the IN clause to append records to a table in another database.

To create a new table, use the [SELECT… INTO](select-into-statement-microsoft-access-sql.md) statement instead to create a make-table query.

To find out which records will be appended before you run the append query, first execute and view the results of a select query that uses the same selection criteria.

An append query copies records from one or more tables to another. The tables that contain the records you append are not affected by the append query.

Instead of appending existing records from another table, you can specify the value for each field in a single new record using the VALUES clause. If you omit the field list, the VALUES clause must include a value for every field in the table; otherwise, the INSERT operation will fail. Use an additional INSERT INTO statement with a VALUES clause for each additional record you want to create.

**Links provided by** the [UtterAccess](https://www.utteraccess.com) community. UtterAccess is the premier Microsoft Access wiki and help forum.

- [Generating sequential numbers for INSERT/UPDATE statements](https://www.utteraccess.com/forum/generating-sequential-num-t446039.html)

- [SQL to VBA Formatter](https://www.utteraccess.com/forum/sql-vba-formatter-t1165308.html)

## Example

This example selects all records in a hypothetical New Customers table and adds them to the Customers table. When individual columns are not designated, the SELECT table column names must match exactly those in the INSERT INTO table.

```vb
    Sub InsertIntoX1() 
     
        Dim dbs As Database 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
         
        ' Select all records in the New Customers table  
        ' and add them to the Customers table. 
        dbs.Execute " INSERT INTO Customers " _ 
            & "SELECT * " _ 
            & "FROM [New Customers];" 
             
        dbs.Close 
     
    End Sub
```


This example creates a new record in the Employees table.

```vb
    Sub InsertIntoX2() 
     
        Dim dbs As Database 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
         
        ' Create a new record in the Employees table. The  
        ' first name is Harry, the last name is Washington,  
        ' and the job title is Trainee. 
        dbs.Execute " INSERT INTO Employees " _ 
            & "(FirstName,LastName, Title) VALUES " _ 
            & "('Harry', 'Washington', 'Trainee');" 
             
        dbs.Close 
     
    End Sub 
```

