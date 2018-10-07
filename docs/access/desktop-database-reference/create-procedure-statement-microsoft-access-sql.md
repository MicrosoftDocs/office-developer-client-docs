---
title: CREATE PROCEDURE Statement (Microsoft Access SQL)
TOCTitle: CREATE PROCEDURE Statement (Microsoft Access SQL)
ms:assetid: 1fbb5267-9862-bfb4-6436-176152d7a6cd
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845861(v=office.15)
ms:contentKeyID: 48543649
ms.date: 09/18/2015
mtps_version: v=office.15
dev_langs:
- sql
---

# CREATE PROCEDURE Statement (Microsoft Access SQL)

**Applies to**: Access 2013 | Office 2013 

Creates a stored procedure.

> [!NOTE]
> The Microsoft Access database engine does not support the use of CREATE PROCEDURE, or any of the DDL statements, with non-Microsoft Jet database engine databases.

## Syntax

CREATE PROCEDURE *procedure* \[*param1 datatype*\[, *param2 datatype*\[, …\]\] AS sqlstatement

The CREATE PROCEDURE statement has these parts:

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
<td><p><em>procedure</em></p></td>
<td><p>A name for the procedure. It must follow standard naming conventions.</p></td>
</tr>
<tr class="even">
<td><p><em>param1</em>, <em>param2</em></p></td>
<td><p>From one to 255 field names or parameters. For example:</p>
<pre class="sourceCode sql" id="cb1"><code class="sourceCode sql"><a class="sourceLine" id="cb1-1" data-line-number="1"><span class="kw">CREATE</span> <span class="kw">PROCEDURE</span> Sales_By_Country [Beginning <span class="dt">Date</span>] DateTime, [Ending <span class="dt">Date</span>] DateTime;</a></code></pre>
<p>For more information on parameters, see <a href="parameters-declaration-microsoft-access-sql.md">PARAMETERS</a>.</p></td>
</tr>
<tr class="odd">
<td><p><em>datatype</em></p></td>
<td><p>One of the primary <a href="sql-data-types.md">Microsoft Access SQL data types</a> or their synonyms.</p></td>
</tr>
<tr class="even">
<td><p><em>sqlstatement</em></p></td>
<td><p>An SQL statement such as SELECT, UPDATE, DELETE, INSERT, CREATE TABLE, DROP TABLE, and so on.</p></td>
</tr>
</tbody>
</table>


## Remarks

An SQL procedure consists of a PROCEDURE clause that specifies the name of the procedure, an optional list of parameter definitions, and a single SQL statement.

A procedure name cannot be the same as the name of an existing table.

## Example

This example names the query CategoryList, and calls the EnumFields procedure, which you can find in the SELECT statement example.

```vb
    Sub ProcedureX() 
     
        Dim dbs As Database, rst As Recordset 
        Dim qdf As QueryDef, strSql As String 
         
        ' Modify this line to include the path to Northwind 
        ' on your computer. 
        Set dbs = OpenDatabase("Northwind.mdb") 
         
        strSql = "PROCEDURE CategoryList; " _ 
            & "SELECT DISTINCTROW CategoryName, " _ 
            & "CategoryID FROM Categories " _ 
            & "ORDER BY CategoryName;" 
         
        ' Create a named QueryDef based on the SQL 
        ' statement. 
        Set qdf = dbs.CreateQueryDef("NewQry", strSql) 
     
        ' Create a temporary snapshot-type Recordset. 
        Set rst = qdf.OpenRecordset(dbOpenSnapshot) 
     
        ' Populate the Recordset. 
        rst.MoveLast 
                 
        ' Call EnumFields to print the contents of the  
        ' Recordset. Pass the Recordset object and desired 
        ' field width. 
        EnumFields rst, 15 
         
        ' Delete the QueryDef because this is a 
        ' demonstration. 
        dbs.QueryDefs.Delete "NewQry" 
         
        dbs.Close 
     
    End Sub
```
