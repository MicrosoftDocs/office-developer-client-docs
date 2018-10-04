---
title: Database.OpenRecordset Method (DAO)
TOCTitle: OpenRecordset Method
ms:assetid: a243bc79-cac4-fe12-768d-d3d017954e78
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff820966(v=office.15)
ms:contentKeyID: 48546753
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052939
f1_categories:
- Office.Version=v15
---

# Database.OpenRecordset Method (DAO)


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Syntax  
Remarks  
Example  
About the Contributors  

Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection.

## Syntax

*expression* .OpenRecordset(***Name***, ***Type***, ***Options***, ***LockEdit***)

*expression* A variable that represents a **Database** object.

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
<td><p>Name</p></td>
<td><p>Required</p></td>
<td><p><strong>String</strong></p></td>
<td><p>The source of the records for the new <strong>Recordset</strong>. The source can be a table name, a query name, or an SQL statement that returns records. For table-type <strong>Recordset</strong> objects in Microsoft Access database engine databases, the source can only be a table name.</p></td>
</tr>
<tr class="even">
<td><p>Type</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong><a href="recordsettypeenum-enumeration-dao.md">RecordsetTypeEnum</a></strong> constant that indicates the type of <strong>Recordset</strong> to open.</p>

> [!NOTE]
> <P>If you open a <STRONG>Recordset</STRONG> in a Microsoft Access workspace and you don't specify a type, <STRONG>OpenRecordset</STRONG> creates a table-type <STRONG>Recordset</STRONG>, if possible. If you specify a linked table or query, <STRONG>OpenRecordset</STRONG> creates a dynaset-type <STRONG>Recordset</STRONG>.</P>


</td>
</tr>
<tr class="odd">
<td><p>Options</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A combination of <strong><a href="recordsetoptionenum-enumeration-dao.md">RecordsetOptionEnum</a></strong> constants that specify characteristics of the new <strong>Recordset</strong>.</p>

> [!NOTE]
> <P>The constants <STRONG>dbConsistent</STRONG> and <STRONG>dbInconsistent</STRONG> are mutually exclusive, and using both causes an error. Supplying a LockEdit argument when Options uses the <STRONG>dbReadOnly</STRONG> constant also causes an error.</P>


</td>
</tr>
<tr class="even">
<td><p>LockEdit</p></td>
<td><p>Optional</p></td>
<td><p><strong>Variant</strong></p></td>
<td><p>A <strong><a href="locktypeenum-enumeration-dao.md">LockTypeEnum</a></strong> constant that determines the locking for the <strong>Recordset</strong>.</p>

> [!NOTE]
> <P>You can use <STRONG>dbReadOnly</STRONG> in either the Options argument or the LockedEdit argument, but not both. If you use it for both arguments, a run-time error occurs.</P>


</td>
</tr>
</tbody>
</table>


### Return Value

Recordset

## Remarks

Typically, if the user gets this error while updating a record, your code should refresh the contents of the fields and retrieve the newly modified values. If the error occurs while deleting a record, your code could display the new record data to the user and a message indicating that the data has recently changed. At this point, your code can request a confirmation that the user still wants to delete the record.

You should also use the **dbSeeChanges** constant if you open a **Recordset** in a Microsoft Access database engine-connected ODBC workspace against a Microsoft SQL Server 6.0 (or later) table that has an IDENTITY column, otherwise an error may result.

Opening more than one **Recordset** on an ODBC data source may fail because the connection is busy with a prior **OpenRecordset** call. One way around this is to fully populate the **Recordset** by using the **MoveLast** method as soon as the **Recordset** is opened.

Closing a **Recordset** with the **[Close](connection-close-method-dao.md)** method automatically deletes it from the **Recordsets** collection.


> [!NOTE]
> <P>If <EM>source</EM> refers to an SQL statement composed of a string concatenated with a non-integer value, and the system parameters specify a non-U.S. decimal character such as a comma (for example, strSQL = "PRICE &gt; " &amp; lngPrice, and lngPrice = 125,50), an error occurs when you try to open the <STRONG>Recordset</STRONG>. This is because during concatenation, the number will be converted to a string using your system's default decimal character, and SQL only accepts U.S. decimal characters.</P>



**Link provided by:**![Community Member Icon](images/Ff193201.8b9774c4-6c97-470e-b3a2-56d8f786444c(Office.15).png "Community Member Icon") The [UtterAccess](http://www.utteraccess.com) community | About the Contributors

  - [Transfer data from Access to Excel](http://www.utteraccess.com/forum/transfer-data-access-ex-t1672619.html)

## Example

The following example shows how to open a Recordset that is based on a parameter query.

**Sample code provided by:** The [Microsoft Access 2010 Programmer’s Reference](http://www.wrox.com/wileycda/wroxtitle/access-2010-programmer-s-reference.productcd-0470591668.html) | About the Contributors

    Dim dbs As DAO.Database
    Dim qdf As DAO.QueryDef
    Dim rst As DAO.Recordset
    
    Set dbs = CurrentDb
    
    'Get the parameter query
    Set qfd = dbs.QueryDefs("qryMyParameterQuery")
    
    'Supply the parameter value
    qdf.Parameters("EnterStartDate") = Date
    qdf.Parameters("EnterEndDate") = Date + 7
    
    'Open a Recordset based on the parameter query
    Set rst = qdf.OpenRecordset()

The following example shows how to open a Recordset based on a table or a query.

    Dim dbs As DAO.Database
    Dim rsTable As DAO.Recordset
    Dim rsQuery As DAO.Recordset
    
    Set dbs = CurrentDb
    
    'Open a table-type Recordset
    Set rsTable = dbs.OpenRecordset("Table1", dbOpenTable)
    
    'Open a dynaset-type Recordset using a saved query
    Set rsQuery = dbs.OpenRecordset("qryMyQuery", dbOpenDynaset)

The following example shows how to open a Recordset based on a Structured Query Language (SQL) statement.

    Dim dbs As DAO.Database
    Dim rsSQL As DAO.Recordset
    Dim strSQL As String
    
    Set dbs = CurrentDb
    
    'Open a snapshot-type Recordset based on an SQL statement
    strSQL = "SELECT * FROM Table1 WHERE Field2 = 33"
    Set rsSQL = dbs.OpenRecordset(strSQL, dbOpenSnapshot)

The following sample shows how to use the Filter property to determine the records to be included in a subsequently opened Recordset.

    Dim dbs As DAO.Database
    Dim rst As DAO.Recordset
    Dim rstFiltered As DAO.Recordset
    Dim strCity As String
    
    Set dbs = CurrentDb
    
    'Create the first filtered Recordset, returning customer records
    'for those visited between 30-60 days ago.
    Set rest = dbs.OpenRecordset(_ 
        "SELECT * FROM Customers WHERE LastVisitDate BETWEEN Date()-60 " & _
        "AND Date()-30 ORDER BY LastVisitDate DESC")
    
    'Begin row processing
    Do While Not rst.EOF
        
        'Retrieve the name of the first city in the selected rows
        strCity = rst!City
    
        'Now filter the Recordset to return only the customers from that city
        rst.Filter = "City = '" & strCity & "'"
        Set rstFiltered = rst.OpenRecordset
    
        'Process the rows
        Do While Not rstFiltered.EOF
            rstFiltered.Edit
            rstFiltered!ToBeVisited = True
            rstFiltered.Update
            rstFiltered.MoveNext
        Loop
    
        'We've done what was needed. Now exit
        Exit Do
        rst.MoveNext
       
    Loop
    
    'Cleanup
    rstFiltered.Close
    rst.Close
    
    Set rstFiltered = Nothing
    Set rst = Nothing

## About the Contributors

UtterAccess is the premier Microsoft Access wiki and help forum. Click here to join.

Wrox Press is driven by the Programmer to Programmer philosophy. Wrox books are written by programmers for programmers, and the Wrox brand means authoritative solutions to real-world programming problems.

