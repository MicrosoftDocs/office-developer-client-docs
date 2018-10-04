---
title: Recordset.FindNext Method (DAO)
TOCTitle: FindNext Method
ms:assetid: 5457dfc8-e561-5624-74d0-34278ba2e7cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff194099(v=office.15)
ms:contentKeyID: 48544893
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.FindNext Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  
About the Contributors  

Locates the next record in a dynaset- or snapshot-type **[Recordset](recordset-object-dao.md)** object that satisfies the specified criteria and makes that record the current record (Microsoft Access workspaces only).

## Syntax

*expression* .FindNext(***Criteria***)

*expression* A variable that represents a **Recordset** object.

### Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/Optional</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Criteria</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>A String used to locate the record. It is like the WHERE clause in an SQL statement, but without the word WHERE.</p></td>
</tr>
</tbody>
</table>


## Remarks

If you want to include all the records in your search — not just those that meet a specific condition — use the **Move** methods to move from record to record. To locate a record in a table-type **Recordset**, use the **Seek** method.

If a record matching the criteria isn't located, the current record pointer is unknown, and the **NoMatch** property is set to **True**. If recordset contains more than one record that satisfies the criteria, **FindFirst** locates the first occurrence, **FindNext** locates the next occurrence, and so on.

Each of the **Find** methods begins its search from the location and in the direction specified in the following table.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Find method</p></th>
<th><p>Begins searching at</p></th>
<th><p>Search direction</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>FindFirst</strong></p></td>
<td><p>Beginning of recordset</p></td>
<td><p>End of recordset</p></td>
</tr>
<tr class="even">
<td><p><strong>FindLast</strong></p></td>
<td><p>End of recordset</p></td>
<td><p>Beginning of recordset</p></td>
</tr>
<tr class="odd">
<td><p><strong>FindNext</strong></p></td>
<td><p>Current record</p></td>
<td><p>End of recordset</p></td>
</tr>
<tr class="even">
<td><p><strong>FindPrevious</strong></p></td>
<td><p>Current record</p></td>
<td><p>Beginning of recordset</p></td>
</tr>
</tbody>
</table>


Using one of the **Find** methods isn't the same as using a **Move** method, however, which simply makes the first, last, next, or previous record current without specifying a condition. You can follow a Find operation with a Move operation.

Always check the value of the **NoMatch** property to determine whether the Find operation has succeeded. If the search succeeds, **NoMatch** is **False**. If it fails, **NoMatch** is **True** and the current record isn't defined. In this case, you must position the current record pointer back to a valid record.

Using the **Find** methods with Microsoft Access database engine-connected ODBC-accessed recordsets can be inefficient. You may find that rephrasing your criteria to locate a specific record is faster, especially when working with large recordsets.

In an ODBCDirect workspace, the **Find** and **Seek** methods are not available on any type of **Recordset** object, because executing a **Find** or **Seek** through an ODBC connection is not very efficient over the network. Instead, you should design the query (that is, using the source argument to the **OpenRecordset** method) with an appropriate WHERE clause that restricts the returned records to only those that meet the criteria you would otherwise use in a **Find** or **Seek** method.

When working with Microsoft Access database engine-connected ODBC databases and large dynaset-type v objects, you might discover that using the **Find** methods or using the **Sort** or **Filter** property is slow. To improve performance, use SQL queries with customized ORDER BY or WHERE clauses, parameter queries, or **QueryDef** objects that retrieve specific indexed records.

You should use the U.S. date format (month-day-year) when you search for fields containing dates, even if you're not using the U.S. version of the Microsoft Access database engine; otherwise, the data may not be found. Use the Visual Basic **Format** function to convert the date. For example:

    rstEmployees.FindFirst "HireDate > #" _ 
        & Format(mydate, 'm-d-yy' ) & "#" 

If criteria is composed of a string concatenated with a non-integer value, and the system parameters specify a non-U.S. decimal character such as a comma (for example, strSQL = "PRICE \> " & lngPrice, and lngPrice = 125,50), an error occurs when you try to call the method. This is because during concatenation, the number will be converted to a string using your system's default decimal character, and Microsoft Access SQL only accepts U.S. decimal characters.


> [!NOTE]
> <UL>
> <LI>
> <P>For best performance, the <EM>criteria</EM> should be in either the form "<EM>field</EM> = <EM>value</EM>" where <EM>field</EM> is an indexed field in the underlying base table, or "<EM>field</EM> LIKE <EM>prefix</EM>" where <EM>field</EM> is an indexed field in the underlying base table and <EM>prefix</EM> is a prefix search string (for example, "ART*" ).</P>
> <LI>
> <P>In general, for equivalent types of searches, the <STRONG>Seek</STRONG> method provides better performance than the <STRONG>Find</STRONG> methods. This assumes that table-type <STRONG>Recordset</STRONG> objects alone can satisfy your needs.</P></LI></UL>



## Example

The following example shows how to use the FindFirst and FindNext methods to find a record in a Recordset.

**Sample code provided by:** The [Microsoft Access 2010 Programmer’s Reference](http://www.wrox.com/wileycda/wroxtitle/access-2010-programmer-s-reference.productcd-0470591668.html) | About the Contributors

    Sub FindOrgName()
    
        Dim dbs As DAO.Database
        Dim rst As DAO.Recordset
        
        'Get the database and Recordset
        Set dbs = CurrentDb
        Set rst = dbs.OpenRecordset("tblCustomers")
    
        'Search for the first matching record   
        rst.FindFirst "[OrgName] LIKE '*parts*'"
        
        'Check the result
        If rst.NoMatch Then
            MsgBox "Record not found."
            GotTo Cleanup
        Else
            Do While Not rst.NoMatch
                MsgBox "Customer name: " & rst!CustName
                rst.FindNext "[OrgName] LIKE '*parts*'"
            Loop
    
            'Search for the next matching record
            rst.FindNext "[OrgName] LIKE '*parts*'"
        End If
       
        Cleanup:
            rst.Close
            Set rst = Nothing
            Set dbs = Nothing
    
    End Sub

## About the Contributors

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems.

