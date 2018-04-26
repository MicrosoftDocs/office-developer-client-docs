---
title: "INNER JOIN Operation (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277574
  
localization_priority: Normal
ms.assetid: 8d16c74c-02c6-12b7-b180-3e7744ef65f3
description: "Combines records from two tables whenever there are matching values in a common field."
---

# INNER JOIN Operation (Microsoft Access SQL)

Combines records from two tables whenever there are matching values in a common field.
  
## Syntax

FROM  *table1*  INNER JOIN  *table2*  ON  *table1*  .  *field1*  *compopr table2*  .  *field2* 
  
The INNER JOIN operation has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *table1*  ,  *table2*  <br/> |The names of the tables from which records are combined.  <br/> |
| *field1*  ,  *field2*  <br/> |The names of the fields that are joined. If they are not numeric, the fields must be of the same data type and contain the same kind of data, but they do not have to have the same name.  <br/> |
| *compopr*  <br/> |Any relational comparison operator: "=," "\<," "\>," "\<=," "\>=," or "\<\>."  <br/> |
   
## Remarks

You can use an INNER JOIN operation in any [FROM](http://msdn.microsoft.com/library/f3c5931e-2768-198e-d69c-095a01c23bb5%28Office.15%29.aspx) clause. This is the most common type of join. Inner joins combine records from two tables whenever there are matching values in a field common to both tables. 
  
You can use INNER JOIN with the Departments and Employees tables to select all the employees in each department. In contrast, to select all departments (even if some have no employees assigned to them) or all employees (even if some are not assigned to a department), you can use a [LEFT JOIN or RIGHT JOIN](left-join-right-join-operations-microsoft-access-sql.md) operation to create an outer join. 
  
If you try to join fields containing Memo or OLE Object data, an error occurs.
  
You can join any two numeric fields of like types. For example, you can join on AutoNumber and Long fields because they are like types. However, you cannot join Single and Double types of fields.
  
The following example shows how you could join the Categories and Products tables on the CategoryID field:
  
```
SELECT CategoryName, ProductName 
FROM Categories INNER JOIN Products 
ON Categories.CategoryID = Products.CategoryID;
```

In the preceding example, CategoryID is the joined field, but it is not included in the query output because it is not included in the [SELECT](select-statement-microsoft-access-sql.md) statement. To include the joined field, include the field name in the SELECT statement — in this case,  `Categories.CategoryID`.
  
You can also link several ON clauses in a JOIN statement, using the following syntax:
  
SELECT  *fields*  FROM  *table1*  INNER JOIN  *table2*  ON  *table1*  .  *field1*  *compopr*  *table2*  .  *field1*  AND ON  *table1*  .  *field2*  *compopr*  *table2*  .  *field2*  ) OR ON  *table1*  .  *field3*  *compopr*  *table2*  .  *field3*  )]; 
  
You can also nest JOIN statements using the following syntax:
  
SELECT  *fields*  FROM  *table1*  INNER JOIN (  *table2*  INNER JOIN [( ]  *table3*  [INNER JOIN [( ]  *tablex*  [INNER JOIN …)] ON  *table3*  .  *field3*  *compopr*  *tablex*  .  *fieldx*  )] ON  *table2*  .  *field2*  *compopr*  *table3*  .  *field3*  ) ON  *table1*  .  *field1*  *compopr*  *table2*  .  *field2*  ; 
  
A LEFT JOIN or a RIGHT JOIN may be nested inside an INNER JOIN, but an INNER JOIN may not be nested inside a LEFT JOIN or a RIGHT JOIN.
  
## Example

This example creates two equi-joins: one between the Order Details and Orders tables and another between the Orders and Employees tables. This is necessary because the Employees table does not contain sales data, and the Order Details table does not contain employee data. The query produces a list of employees and their total sales.
  
This example calls the EnumFields procedure, which you can find in the SELECT statement example.
  
```
Sub InnerJoinX() 
 
    Dim dbs As Database, rst As Recordset 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    ' Create a join between the Order Details and  
    ' Orders tables and another between the Orders and  
    ' Employees tables. Get a list of employees and  
    ' their total sales. 
    Set rst = dbs.OpenRecordset("SELECT DISTINCTROW " _ 
        &amp; "Sum(UnitPrice * Quantity) AS Sales, " _ 
        &amp; "(FirstName &amp; Chr(32) &amp; LastName) AS Name " _ 
        &amp; "FROM Employees INNER JOIN(Orders " _ 
        &amp; "INNER JOIN [Order Details] " _ 
        &amp; "ON [Order Details].OrderID = " _ 
        &amp; "Orders.OrderID ) " _ 
        &amp; "ON Orders.EmployeeID = " _ 
        &amp; "Employees.EmployeeID " _ 
        &amp; "GROUP BY (FirstName &amp; Chr(32) &amp; LastName);") 
     
    ' Populate the Recordset. 
    rst.MoveLast 
     
    ' Call EnumFields to print the contents of the  
    ' Recordset. Pass the Recordset object and desired 
    ' field width. 
    EnumFields rst, 20 
 
    dbs.Close 
 
End Sub 

```


