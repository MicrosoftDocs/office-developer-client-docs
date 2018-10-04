---
title: DELETE Statement (Microsoft Access SQL)
TOCTitle: DELETE Statement (Microsoft Access SQL)
ms:assetid: 64c235bc-5b1a-0a33-714a-9933ba7a81e5
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195097(v=office.15)
ms:contentKeyID: 48545299
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277573
f1_categories:
- Office.Version=v15
---

# DELETE Statement (Microsoft Access SQL)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Remarks  
Example  

Creates a delete query that removes records from one or more of the tables listed in the [FROM](https://msdn.microsoft.com/library/ff836674\(v=office.15\)) clause that satisfy the [WHERE](https://msdn.microsoft.com/library/ff195245\(v=office.15\)) clause.

## Syntax

DELETE \[*table*.\*\] FROM *table* WHERE *criteria*

The DELETE statement has these parts:

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
<td><p><em>table</em></p></td>
<td><p>The optional name of the table from which records are deleted.</p></td>
</tr>
<tr class="even">
<td><p><em>table</em></p></td>
<td><p>The name of the table from which records are deleted.</p></td>
</tr>
<tr class="odd">
<td><p><em>criteria</em></p></td>
<td><p>An expression that determines which records to delete.</p></td>
</tr>
</tbody>
</table>


## Remarks

DELETE is especially useful when you want to delete many records.

To drop an entire table from the database, you can use the **Execute** method with a [DROP](drop-statement-microsoft-access-sql.md) statement. If you delete the table, however, the structure is lost. In contrast, when you use DELETE, only the data is deleted; the table structure and all of the table properties, such as field attributes and indexes, remain intact.

You can use DELETE to remove records from tables that are in a one-to-many relationship with other tables. Cascade delete operations cause the records in tables that are on the many side of the relationship to be deleted when the corresponding record in the one side of the relationship is deleted in the query. For example, in the relationship between the Customers and Orders tables, the Customers table is on the one side and the Orders table is on the many side of the relationship. Deleting a record from Customers results in the corresponding Orders records being deleted if the cascade delete option is specified.

A delete query deletes entire records, not just data in specific fields. If you want to delete values in a specific field, create an update query that changes the values to **Null**.


> [!IMPORTANT]
> <UL>
> <LI>
> <P>After you remove records using a delete query, you cannot undo the operation. If you want to know which records were deleted, first examine the results of a select query that uses the same criteria, and then run the delete query.</P>
> <LI>
> <P>Maintain backup copies of your data at all times. If you delete the wrong records, you can retrieve them from your backup copies.</P></LI></UL>



## Example

This example deletes all records for employees whose title is Trainee. When the FROM clause includes only one table, you do not have to list the table name in the DELETE statement.

    Sub DeleteX() 
     
        Dim dbs As Database, rst As Recordset 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
     
        ' Delete employee records where title is Trainee.     
        dbs.Execute "DELETE * FROM " _ 
            & "Employees WHERE Title = 'Trainee';" 
         
        dbs.Close 
     
    End Sub

