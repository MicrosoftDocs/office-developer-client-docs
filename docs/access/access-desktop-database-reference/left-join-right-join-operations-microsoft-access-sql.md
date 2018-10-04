---
title: LEFT JOIN, RIGHT JOIN Operations (Microsoft Access SQL)
TOCTitle: LEFT JOIN, RIGHT JOIN Operations (Microsoft Access SQL)
ms:assetid: 9c10525f-98b1-fd4f-8b40-07a32c5c6502
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff198084(v=office.15)
ms:contentKeyID: 48546586
ms.date: 09/18/2015
mtps_version: v=office.15
dev_langs:
- sql
---

# LEFT JOIN, RIGHT JOIN Operations (Microsoft Access SQL)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Remarks  
Example  

Combines source-table records when used in any [FROM](https://msdn.microsoft.com/en-us/library/ff836674\(v=office.15\)) clause.

## Syntax

FROM *table1* \[ LEFT | RIGHT \] JOIN *table2* ON *table1.field1* *compopr table2.field2*

The LEFT JOIN and RIGHT JOIN operations have these parts:

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
<td><p><em>table1</em>, <em>table2</em></p></td>
<td><p>The names of the tables from which records are combined.</p></td>
</tr>
<tr class="even">
<td><p><em>field1</em>, <em>field2</em></p></td>
<td><p>The names of the fields that are joined. The fields must be of the same data type and contain the same kind of data, but they do not need to have the same name.</p></td>
</tr>
<tr class="odd">
<td><p><em>compopr</em></p></td>
<td><p>Any relational comparison operator: &quot;=,&quot; &quot;&lt;,&quot; &quot;&gt;,&quot; &quot;&lt;=,&quot; &quot;&gt;=,&quot; or &quot;&lt;&gt;.&quot;</p></td>
</tr>
</tbody>
</table>


## Remarks

Use a LEFT JOIN operation to create a left outer join. Left outer joins include all of the records from the first (left) of two tables, even if there are no matching values for records in the second (right) table.

Use a RIGHT JOIN operation to create a right outer join. Right outer joins include all of the records from the second (right) of two tables, even if there are no matching values for records in the first (left) table.

For example, you could use LEFT JOIN with the Departments (left) and Employees (right) tables to select all departments, including those that have no employees assigned to them. To select all employees, including those who are not assigned to a department, you would use RIGHT JOIN.

The following example shows how you could join the Categories and Products tables on the CategoryID field. The query produces a list of all categories, including those that contain no products:

``` sql
SELECT CategoryName, 
ProductName 
FROM Categories LEFT JOIN Products 
ON Categories.CategoryID = Products.CategoryID;
```

In this example, CategoryID is the joined field, but it is not included in the query results because it is not included in the [SELECT](select-statement-microsoft-access-sql.md) statement. To include the joined field, enter the field name in the SELECT statement — in this case, Categories.CategoryID.


> [!NOTE]
> <UL>
> <LI>
> <P>To create a query that includes only records in which the data in the joined fields is the same, use an <A href="inner-join-operation-microsoft-access-sql.md">INNER JOIN</A> operation.</P>
> <LI>
> <P>A LEFT JOIN or a RIGHT JOIN can be nested inside an INNER JOIN, but an INNER JOIN cannot be nested inside a LEFT JOIN or a RIGHT JOIN. See the discussion of nesting in the INNER JOIN topic to see how to nest joins within other joins.</P>
> <LI>
> <P>You can link multiple ON clauses. See the discussion of clause linking in the INNER JOIN topic to see how this is done.</P>
> <LI>
> <P>If you try to join fields containing Memo or OLE Object data, an error occurs.</P></LI></UL>



## Example

This example assumes the existence of hypothetical Department Name and Department ID fields in an Employees table. Note that these fields do not actually exist in the Northwind database Employees table.

This example selects all departments, including those without employees.

This example calls the EnumFields procedure, which you can find in the SELECT statement example.

    Sub LeftRightJoinX() 
     
        Dim dbs As Database, rst As Recordset 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
         
        ' Select all departments, including those  
        ' without employees. 
        Set rst = dbs.OpenRecordset _ 
            ("SELECT [Department Name], " _ 
            & "FirstName & Chr(32) & LastName AS Name " _ 
            & "FROM Departments LEFT JOIN Employees " _ 
            & "ON Departments.[Department ID] = " _ 
            & "Employees.[Department ID] " _ 
            & "ORDER BY [Department Name];") 
         
        ' Populate the Recordset. 
        rst.MoveLast 
         
        ' Call EnumFields to print the contents of the  
        ' Recordset. Pass the Recordset object and desired 
        ' field width. 
        EnumFields rst, 20 
     
        dbs.Close 
     
    End Sub

