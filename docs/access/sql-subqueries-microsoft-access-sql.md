---
title: "SQL Subqueries (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277580
  
localization_priority: Normal
ms.assetid: 3b6c0a5d-ab24-e1cf-0175-3f8e68c2dfbf
description: "A subquery is a SELECT statement nested inside a SELECT, SELECT…INTO, INSERT…INTO, DELETE, or UPDATE statement or inside another subquery."
---

# SQL Subqueries (Microsoft Access SQL)

A subquery is a [SELECT](select-statement-microsoft-access-sql.md) statement nested inside a SELECT, [SELECT…INTO](select-into-statement-microsoft-access-sql.md), [INSERT…INTO](insert-into-statement-microsoft-access-sql.md), [DELETE](delete-statement-microsoft-access-sql.md), or [UPDATE](update-statement-microsoft-access-sql.md) statement or inside another subquery. 
  
## Syntax

You can use three forms of syntax to create a subquery:
  
 *comparison*  [ANY | ALL | SOME] (  *sqlstatement*  ) 
  
 *expression*  [NOT] IN (  *sqlstatement*  ) 
  
[NOT] EXISTS ( *sqlstatement*  ) 
  
A subquery has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *comparison*  <br/> |An expression and a comparison operator that compares the expression with the results of the subquery.  <br/> |
| *expression*  <br/> |An expression for which the result set of the subquery is searched.  <br/> |
| *sqlstatement*  <br/> |A SELECT statement, following the same format and rules as any other SELECT statement. It must be enclosed in parentheses.  <br/> |
   
## Remarks

You can use a subquery instead of an expression in the field list of a SELECT statement or in a [WHERE](http://msdn.microsoft.com/library/67e4caed-6512-e8bd-39d0-6dca18114b18%28Office.15%29.aspx) or [HAVING](http://msdn.microsoft.com/library/4fc4655b-c8a6-2ca2-509e-ac98d9a1c776%28Office.15%29.aspx) clause. In a subquery, you use a SELECT statement to provide a set of one or more specific values to evaluate in the WHERE or HAVING clause expression. 
  
Use the ANY or SOME predicate, which are synonymous, to retrieve records in the main query that satisfy the comparison with any records retrieved in the subquery. The following example returns all products whose unit price is greater than that of any product sold at a discount of 25 percent or more:
  
```
SELECT * FROM Products 
WHERE UnitPrice > ANY 
(SELECT UnitPrice FROM OrderDetails 
WHERE Discount >= .25);
```

Use the [ALL](http://msdn.microsoft.com/library/6ff5c418-897b-7d65-8551-5a0ace3c587f%28Office.15%29.aspx) predicate to retrieve only those records in the main query that satisfy the comparison with all records retrieved in the subquery. If you changed ANY to ALL in the previous example, the query would return only those products whose unit price is greater than that of all products sold at a discount of 25 percent or more. This is much more restrictive. 
  
Use the IN predicate to retrieve only those records in the main query for which some record in the subquery contains an equal value. The following example returns all products with a discount of 25 percent or more:
  
```
SELECT * FROM Products 
WHERE ProductID IN 
(SELECT ProductID FROM OrderDetails 
WHERE Discount >= .25);
```

Conversely, you can use NOT IN to retrieve only those records in the main query for which no record in the subquery contains an equal value.
  
Use the EXISTS predicate (with the optional NOT reserved word) in true/false comparisons to determine whether the subquery returns any records.
  
You can also use table name aliases in a subquery to refer to tables listed in a [FROM](http://msdn.microsoft.com/library/f3c5931e-2768-198e-d69c-095a01c23bb5%28Office.15%29.aspx) clause outside the subquery. The following example returns the names of employees whose salaries are equal to or greater than the average salary of all employees having the same job title. The Employees table is given the alias "T1": 
  
```
SELECT LastName,
FirstName, Title, Salary 
FROM Employees AS T1 
WHERE Salary >= (SELECT Avg(Salary) 
FROM Employees 
WHERE T1.Title = Employees.Title) Order by Title;
```

In the preceding example, the AS reserved word is optional.
  
Some subqueries are allowed in crosstab queries— specifically, as predicates (those in the WHERE clause). Subqueries as output (those in the SELECT list) are not allowed in crosstab queries.
  
## Example

This example lists the name and contact of every customer who placed an order in the second quarter of 1995.
  
This example calls the EnumFields procedure, which you can find in the SELECT statement example.
  
```
Sub SubQueryX() 
 
    Dim dbs As Database, rst As Recordset 
 
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
     
    ' List the name and contact of every customer  
    ' who placed an order in the second quarter of 
    ' 1995. 
    Set rst = dbs.OpenRecordset("SELECT ContactName," _ 
        &amp; " CompanyName, ContactTitle, Phone" _ 
        &amp; " FROM Customers" _ 
        &amp; " WHERE CustomerID" _ 
        &amp; " IN (SELECT CustomerID FROM Orders" _ 
        &amp; " WHERE OrderDate Between #04/1/95#" _ 
        &amp; " And #07/1/95#);") 
     
    ' Populate the Recordset. 
    rst.MoveLast 
     
    ' Call EnumFields to print the contents of the  
    ' Recordset. Pass the Recordset object and desired 
    ' field width. 
    EnumFields rst, 25 
 
    dbs.Close 
 
End Sub
```


