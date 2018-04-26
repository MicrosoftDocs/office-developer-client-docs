---
title: "TRANSFORM Statement (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277581
  
localization_priority: Normal
ms.assetid: 419770b1-c833-959d-a84d-56c68764799f
description: "Creates a crosstab query."
---

# TRANSFORM Statement (Microsoft Access SQL)

Creates a crosstab query.
  
## Syntax

TRANSFORM  *aggfunction*  *selectstatement*  PIVOT  *pivotfield*  [IN (  *value1*  [,  *value2*  [, …]])] 
  
The TRANSFORM statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *aggfunction*  <br/> |An [SQL aggregate function](sql-aggregate-functions-sql.md) that operates on the selected data.  <br/> |
| *selectstatement*  <br/> |A [SELECT](select-statement-microsoft-access-sql.md) statement.  <br/> |
| *pivotfield*  <br/> |The field or expression you want to use to create column headings in the query's result set.  <br/> |
| *value1*  ,  *value2*  <br/> |Fixed values used to create column headings.  <br/> |
   
## Remarks

When you summarize data using a crosstab query, you select values from specified fields or expressions as column headings so you can view data in a more compact format than with a select query.
  
TRANSFORM is optional but when included is the first statement in an SQL string. It precedes a SELECT statement that specifies the fields used as row headings and a [GROUP BY](http://msdn.microsoft.com/library/fe7d5e27-a47a-1229-232c-cf6a0cbad761%28Office.15%29.aspx) clause that specifies row grouping. Optionally, you can include other clauses, such as [WHERE](http://msdn.microsoft.com/library/67e4caed-6512-e8bd-39d0-6dca18114b18%28Office.15%29.aspx), that specify additional selection or sorting criteria. You can also use subqueries as predicates — specifically, those in the WHERE clause — in a crosstab query.
  
The values returned in  *pivotfield*  are used as column headings in the query's result set. For example, pivoting the sales figures on the month of the sale in a crosstab query would create 12 columns. You can restrict  *pivotfield*  to create headings from fixed values (  *value1*  ,  *value2*  ) listed in the optional IN clause. You can also include fixed values for which no data exists to create additional columns. 
  
## Example

This example uses the SQL TRANSFORM clause to create a crosstab query showing the number of orders taken by each employee for each calendar quarter of 1994. The SQLTRANSFORMOutput function is required for this procedure to run.
  
```
Sub TransformX1() 
 
    Dim dbs As Database 
    Dim strSQL As String 
    Dim qdfTRANSFORM As QueryDef 
 
    strSQL = "PARAMETERS prmYear SHORT; TRANSFORM " _ 
        &amp; "Count(OrderID) " _ 
        &amp; "SELECT FirstName &amp; "" "" &amp; LastName AS " _ 
        &amp; "FullName FROM Employees INNER JOIN Orders " _ 
        &amp; "ON Employees.EmployeeID = " _ 
        &amp; "Orders.EmployeeID WHERE DatePart " _ 
        &amp; "(""yyyy"", OrderDate) = [prmYear] " 
   
       strSQL = strSQL &amp; "GROUP BY FirstName &amp; " _ 
        &amp; """ "" &amp; LastName " _ 
        &amp; "ORDER BY FirstName &amp; "" "" &amp; LastName " _ 
        &amp; "PIVOT DatePart(""q"", OrderDate)" 
     
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
 
    Set qdfTRANSFORM = dbs.CreateQueryDef _ 
        ("", strSQL) 
     
    SQLTRANSFORMOutput qdfTRANSFORM, 1994 
     
    dbs.Close 
 
End Sub
```

This example uses the SQL TRANSFORM clause to create a slightly more complex crosstab query showing the total dollar amount of orders taken by each employee for each calendar quarter of 1994. The SQLTRANSFORMOutput function is required for this procedure to run.
  
```
Sub TransformX2() 
 
    Dim dbs As Database 
    Dim strSQL As String 
    Dim qdfTRANSFORM As QueryDef 
 
    strSQL = "PARAMETERS prmYear SMALLINT; TRANSFORM " _ 
        &amp; "Sum(Subtotal) SELECT FirstName &amp; "" """ _ 
        &amp; "&amp; LastName AS FullName " _ 
        &amp; "FROM Employees INNER JOIN " _ 
        &amp; "(Orders INNER JOIN [Order Subtotals] " _ 
        &amp; "ON Orders.OrderID = " _ 
        &amp; "[Order Subtotals].OrderID) " _ 
        &amp; "ON Employees.EmployeeID = " _ 
        &amp; "Orders.EmployeeID WHERE DatePart" _ 
        &amp; "(""yyyy"", OrderDate) = [prmYear] " 
    
       strSQL = strSQL &amp; "GROUP BY FirstName &amp; "" """ _ 
        &amp; "&amp; LastName " _ 
        &amp; "ORDER BY FirstName &amp; "" "" &amp; LastName " _ 
        &amp; "PIVOT DatePart(""q"",OrderDate)"         
         
    ' Modify this line to include the path to Northwind 
    ' on your computer. 
    Set dbs = OpenDatabase("Northwind.mdb") 
 
    Set qdfTRANSFORM = dbs.CreateQueryDef _ 
        ("", strSQL) 
     
    SQLTRANSFORMOutput qdfTRANSFORM, 1994 
     
    dbs.Close 
 
End Sub 
 
Function SQLTRANSFORMOutput(qdfTemp As QueryDef, _ 
    intYear As Integer) 
     
    Dim rstTRANSFORM As Recordset 
    Dim fldLoop As Field 
    Dim booFirst As Boolean 
 
    qdfTemp.PARAMETERS!prmYear = intYear 
    Set rstTRANSFORM = qdfTemp.OpenRecordset() 
     
    Debug.Print qdfTemp.SQL 
    Debug.Print 
    Debug.Print , , "Quarter" 
 
    With rstTRANSFORM 
        booFirst = True 
        For Each fldLoop In .Fields 
            If booFirst = True Then 
                Debug.Print fldLoop.Name 
                Debug.Print , ; 
                booFirst = False 
            Else 
                Debug.Print , fldLoop.Name; 
            End If 
        Next fldLoop 
        Debug.Print 
         
        Do While Not .EOF 
            booFirst = True 
            For Each fldLoop In .Fields 
                If booFirst = True Then 
                    Debug.Print fldLoop 
                    Debug.Print , ; 
                    booFirst = False 
                Else 
                    Debug.Print , fldLoop; 
                End If 
            Next fldLoop 
            Debug.Print 
            .MoveNext 
        Loop 
    End With 
     
End Function
```


