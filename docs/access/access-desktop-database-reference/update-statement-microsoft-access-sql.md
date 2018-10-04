---
title: UPDATE Statement (Microsoft Access SQL)
TOCTitle: UPDATE Statement (Microsoft Access SQL)
ms:assetid: 08f9c3d6-c020-ecf1-5748-43b93a76dfbb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff845036(v=office.15)
ms:contentKeyID: 48543111
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277583
dev_langs:
- sql
f1_categories:
- Office.Version=v15
---

# UPDATE Statement (Microsoft Access SQL)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  

Creates an update query that changes values in fields in a specified table based on specified criteria.

## Syntax

UPDATE *table* SET *newvalue* WHERE *criteria*;

The UPDATE statement has these parts:

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
<td><p>The name of the table containing the data you want to modify.</p></td>
</tr>
<tr class="even">
<td><p><em>newvalue</em></p></td>
<td><p>An expression that determines the value to be inserted into a particular field in the updated records.</p></td>
</tr>
<tr class="odd">
<td><p><em>criteria</em></p></td>
<td><p>An expression that determines which records will be updated. Only records that satisfy the expression are updated.</p></td>
</tr>
</tbody>
</table>


## Remarks

UPDATE is especially useful when you want to change many records or when the records that you want to change are in multiple tables.

You can change several fields at the same time. The following example increases the Order Amount values by 10 percent and the Freight values by 3 percent for shippers in the United Kingdom:

``` sql
UPDATE Orders 
SET OrderAmount = OrderAmount * 1.1, 
Freight = Freight * 1.03 
WHERE ShipCountry = 'UK';
```


> [!IMPORTANT]
> <UL>
> <LI>
> <P>UPDATE does not generate a result set. Also, after you update records using an update query, you cannot undo the operation. If you want to know which records were updated, first examine the results of a select query that uses the same criteria, and then run the update query.</P>
> <LI>
> <P>Maintain backup copies of your data at all times. If you update the wrong records, you can retrieve them from your backup copies.</P></LI></UL>



## Example

This example changes values in the ReportsTo field to 5 for all employee records that currently have ReportsTo values of 2.

    Sub UpdateX() 
     
        Dim dbs As Database 
        Dim qdf As QueryDef 
     
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
         
        ' Change values in the ReportsTo field to 5 for all  
        ' employee records that currently have ReportsTo  
        ' values of 2. 
        dbs.Execute "UPDATE Employees " _ 
            & "SET ReportsTo = 5 " _ 
            & "WHERE ReportsTo = 2;" 
             
        dbs.Close 
     
    End Sub

