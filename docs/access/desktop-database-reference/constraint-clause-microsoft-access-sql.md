---
title: CONSTRAINT clause (Microsoft Access SQL)
TOCTitle: CONSTRAINT clause (Microsoft Access SQL)
ms:assetid: f8e89a91-a69e-1811-42a7-921692110bcb
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836971(v=office.15)
ms:contentKeyID: 48548797
ms.date: 10/18/2018
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277561
dev_langs:
- sql
f1_categories:
- Office.Version=v15
ms.localizationpriority: high
---

# CONSTRAINT clause (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

A constraint is similar to an index, although it can also be used to establish a relationship with another table.

You use the CONSTRAINT clause in [ALTER TABLE](alter-table-statement-microsoft-access-sql.md) and [CREATE TABLE](create-table-statement-microsoft-access-sql.md) statements to create or delete constraints. There are two types of CONSTRAINT clauses: one for creating a constraint on a single field and one for creating a constraint on more than one field.

> [!NOTE]
> The Microsoft Access database engine does not support the use of CONSTRAINT, or any of the data definition language (DDL) statements, with non-Microsoft Access database engine databases. Use the DAO **Create** methods instead.

## Syntax

### Single-field constraint

CONSTRAINT *name* {PRIMARY KEY | UNIQUE | NOT NULL | REFERENCES *foreigntable* \[(*foreignfield1, foreignfield2*)\] \[ON UPDATE CASCADE | SET NULL\] \[ON DELETE CASCADE | SET NULL\]}

### Multiple-field constraint

CONSTRAINT *name* {PRIMARY KEY (*primary1*\[, *primary2* \[, …\]\]) | UNIQUE (*unique1*\[, *unique2* \[, …\]\]) | NOT NULL (*notnull1*\[, *notnull2* \[, …\]\]) | FOREIGN KEY \[NO INDEX\] (*ref1*\[, *ref2* \[, …\]\]) REFERENCES *foreigntable* \[(*foreignfield1* \[, *foreignfield2* \[, …\]\])\] \[ON UPDATE CASCADE | SET NULL\] \[ON DELETE CASCADE | SET NULL\]}

The CONSTRAINT clause has these parts:

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
<td><p><em>name</em></p></td>
<td><p>The name of the constraint to be created.</p></td>
</tr>
<tr class="even">
<td><p><em>primary1</em>, <em>primary2</em></p></td>
<td><p>The name of the field or fields to be designated the primary key.</p></td>
</tr>
<tr class="odd">
<td><p><em>unique1</em>, <em>unique2</em></p></td>
<td><p>The name of the field or fields to be designated as a unique key.</p></td>
</tr>
<tr class="even">
<td><p><em>notnull1, notnull2</em></p></td>
<td><p>The name of the field or fields that are restricted to non-Null values.</p></td>
</tr>
<tr class="odd">
<td><p><em>ref1</em>, <em>ref2</em></p></td>
<td><p>The name of a foreign key field or fields that refer to fields in another table.</p></td>
</tr>
<tr class="even">
<td><p><em>foreigntable</em></p></td>
<td><p>The name of the foreign table containing the field or fields specified by <em>foreignfield</em>.</p></td>
</tr>
<tr class="odd">
<td><p><em>foreignfield1</em>, <em>foreignfield2</em></p></td>
<td><p>The name of the field or fields in <em>foreigntable</em> specified by <em>ref1</em>, <em>ref2</em>. You can omit this clause if the referenced field is the primary key of <em>foreigntable</em>.</p></td>
</tr>
</tbody>
</table>


## Remarks

You use the syntax for a single-field constraint in the field-definition clause of an ALTER TABLE or CREATE TABLE statement immediately following the specification of the field's data type.

You use the syntax for a multiple-field constraint whenever you use the reserved word CONSTRAINT outside a field-definition clause in an ALTER TABLE or CREATE TABLE statement.

Using CONSTRAINT you can designate a field as one of the following types of constraints:

- You can use the UNIQUE reserved word to designate a field as a unique key. This means that no two records in the table can have the same value in this field. You can constrain any field or list of fields as unique. If a multiple-field constraint is designated as a unique key, the combined values of all fields in the index must be unique, even if two or more records have the same value in just one of the fields.

- You can use the PRIMARY KEY reserved words to designate one field or set of fields in a table as a primary key. All values in the primary key must be unique and not **Null**, and there can be only one primary key for a table.
    
  > [!NOTE]
  > Do not set a PRIMARY KEY constraint on a table that already has a primary key; if you do, an error occurs.

- You can use the FOREIGN KEY reserved words to designate a field as a foreign key. If the foreign table's primary key consists of more than one field, you must use a multiple-field constraint definition, listing all of the referencing fields, the name of the foreign table, and the names of the referenced fields in the foreign table in the same order that the referencing fields are listed. If the referenced field or fields are the foreign table's primary key, you do not have to specify the referenced fields. By default the database engine behaves as if the foreign table's primary key is the referenced fields. Foreign key constraints define specific actions to be performed when a corresponding primary key value is changed:

- You can specify actions to be performed on the foreign table based on a corresponding action performed on a primary key in the table on which the CONSTRAINT is defined. For example, consider the following definition for the table Customers:
    
  ``` sql
    CREATE TABLE Customers (CustId INTEGER PRIMARY KEY, CLstNm NCHAR VARYING (50))
  ```
    
  Consider the following definition of the table Orders, which defines a foreign key relationship referencing the primary key of the Customers table:
    
  ``` sql
    CREATE TABLE Orders (OrderId INTEGER PRIMARY KEY, CustId INTEGER, OrderNotes NCHAR VARYING (255), CONSTRAINT FKOrdersCustId FOREIGN KEY (CustId) REFERENCES Customers ON UPDATE CASCADE ON DELETE CASCADE
  ```
    
  Both an ON UPDATE CASCADE and an ON DELETE CASCADE clause are defined on the foreign key. The ON UPDATE CASCADE clause means that if a customer's identifier (CustId) is updated in the Customer table, the update will be cascaded through the Orders table. Each order containing a corresponding customer identifier value will be updated automatically with the new value. The ON DELETE CASCADE clause means that if a customer is deleted from the Customer table, all rows in the Orders table containing the same customer identifier value will also be deleted. Consider the following different definition of the table Orders, using the SET NULL action instead of the CASCADE action:
  
  ``` sql
    CREATE TABLE Orders (OrderId INTEGER PRIMARY KEY, CustId INTEGER, OrderNotes NCHAR VARYING (255), CONSTRAINT FKOrdersCustId FOREIGN KEY (CustId) REFERENCES Customers ON UPDATE SET NULL ON DELETE SET NULL
  ```
    
  The ON UPDATE SET NULL clause means that if a customer's identifier (CustId) is updated in the Customer table, the corresponding foreign key values in the Orders table will automatically be set to NULL. Similarly, the ON DELETE SET NULL clause means that if a customer is deleted from the Customer table, all corresponding foreign keys in the Orders table will automatically be set to NULL.

To prevent the automatic creation of indexes for foreign keys, the modifier NO INDEX can be used. This form of foreign key definition should be used only in cases where the resulting index values would be frequently duplicated. Where the values in a foreign key index are frequently duplicated, using an index can be less efficient than simply performing a table scan. Maintaining this type of index, with rows inserted and deleted from the table, degrades performance and does not provide any benefit.

## Example

This example creates a new table called ThisTable with two text fields.

```vb 
 Sub CreateTableX1()    
Dim dbs As Database 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
 
    ' Create a table with two text fields. 
    dbs.Execute "CREATE TABLE ThisTable " _ 
        & "(FirstName CHAR, LastName CHAR);" 
 
    dbs.Close 
 
End Sub
```


This example creates a new table called MyTable with two text fields, a Date/Time field, and a unique index made up of all three fields.

```vb
    Sub CreateTableX2() 
     
        Dim dbs As Database 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
     
        Set dbs = OpenDatabase("Northwind.mdb") 
     
        ' Create a table with three fields and a unique 
        ' index made up of all three fields. 
        dbs.Execute "CREATE TABLE MyTable " _ 
            & "(FirstName CHAR, LastName CHAR, " _ 
            & "DateOfBirth DATETIME, " _ 
            & "CONSTRAINT MyTableConstraint UNIQUE " _ 
            & "(FirstName, LastName, DateOfBirth));" 
     
        dbs.Close 
     
    End Sub
```


This example creates a new table with two text fields and an **Integer** field. The SSN field is the primary key.

```vb
    Sub CreateTableX3() 
     
         Dim dbs As Database 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
     
        ' Create a table with three fields and a primary 
        ' key. 
        dbs.Execute "CREATE TABLE NewTable " _ 
            & "(FirstName CHAR, LastName CHAR, " _ 
            & "SSN INTEGER CONSTRAINT MyFieldConstraint " _ 
            & "PRIMARY KEY);" 
     
        dbs.Close 
     
    End Sub
```


