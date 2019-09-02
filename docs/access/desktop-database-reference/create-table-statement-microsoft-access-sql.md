---
title: CREATE TABLE statement (Microsoft Access SQL)
TOCTitle: CREATE TABLE statement (Microsoft Access SQL)
ms:assetid: fc45d36e-6e43-c030-5016-cca8bb1379fe
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837200(v=office.15)
ms:contentKeyID: 48548888
ms.date: 09/03/2019
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277563
f1_categories:
- Office.Version=v15
localization_priority: Priority
---

# CREATE TABLE statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Creates a new table.

> [!NOTE]
> The Microsoft Access database engine does not support the use of CREATE TABLE, or any of the DDL statements, with non-Microsoft Access database engine databases. Use the DAO **Create** methods instead.

## Syntax

CREATE \[TEMPORARY\] TABLE *table* (*field1 type* \[(*size*)\] \[NOT NULL\] \[WITH COMPRESSION | WITH COMP\] \[*index1*\] \[, *field2* *type* \[(*size*)\] \[NOT NULL\] \[*index2*\] \[, …\]\] \[, CONSTRAINT *multifieldindex* \[, …\]\])

The CREATE TABLE statement has these parts:

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
<td><p>The name of the table to be created.</p></td>
</tr>
<tr class="even">
<td><p><em>field1</em>, <em>field2</em></p></td>
<td><p>The name of field or fields to be created in the new table. You must create at least one field.</p></td>
</tr>
<tr class="odd">
<td><p><em>type</em></p></td>
<td><p>The data type of <em>field</em> in the new table.</p></td>
</tr>
<tr class="even">
<td><p><em>size</em></p></td>
<td><p>The field size in characters (Text and Binary fields only).</p></td>
</tr>
<tr class="odd">
<td><p><em>index1</em>, <em>index2</em></p></td>
<td><p>A CONSTRAINT clause defining a single-field index. For more information about how to create this index, see <a href="constraint-clause-microsoft-access-sql.md">CONSTRAINT clause</a>.</p></td>
</tr>
<tr class="even">
<td><p><em>multifieldindex</em></p></td>
<td><p>A CONSTRAINT clause defining a multiple-field index. For more information about how to create this index, see <a href="constraint-clause-microsoft-access-sql.md">CONSTRAINT clause</a>.</p></td>
</tr>
</tbody>
</table>


## Remarks

Use the CREATE TABLE statement to define a new table and its fields and field constraints. If NOT NULL is specified for a field, new records are required to have valid data in that field.

A CONSTRAINT clause establishes various restrictions on a field, and can be used to establish the primary key. You can also use the [CREATE INDEX](create-index-statement-microsoft-access-sql.md) statement to create a primary key or additional indexes on existing tables.

You can use NOT NULL on a single field or within a named CONSTRAINT clause that applies to either a single field or to a multiple-field named CONSTRAINT. However, you can apply the NOT NULL restriction only once to a field. Attempting to apply this restriction more than once results in a run-time error.

When a TEMPORARY table is created, it is visible only within the session in which it was created. It is automatically deleted when the session is terminated. Temporary tables can be accessed by more than one user.

The WITH COMPRESSION attribute can be used only with the CHARACTER and MEMO (also known as TEXT) data types and their synonyms.

The WITH COMPRESSION attribute was added for CHARACTER columns because of the change to the Unicode character representation format. Unicode characters uniformly require two bytes for each character. For existing Microsoft Jet databases that contain predominately character data, this could mean that the database file would nearly double in size when converted to the Microsoft Access database engine format. However, Unicode representation of many character sets, those formerly denoted as Single-Byte Character Sets (SBCS), can easily be compressed to a single byte. If you define a CHARACTER column with this attribute, data will automatically be compressed as it is stored and uncompressed when retrieved from the column.

MEMO columns can also be defined to store data in a compressed format. However, there is a limitation. Only instances of MEMO columns that, when compressed, will fit within 4096 bytes or less, will be compressed. All other instances of MEMO columns will remain uncompressed. This means that within a given table, for a given MEMO column, some data may be compressed and some data may not be compressed.

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

<br/>

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

<br/>

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

<br/>

This example creates a new table called `~~Kitsch'n Sync` that demonstrates all the different field and index types. The AutoNumber field is the primary key.

```vb
    Sub CreateTableX6()
        On Error Resume Next
        Application.CurrentDb.Execute "Drop Table [~~Kitsch'n Sync];"
        On Error GoTo 0
        
        'This example uses ADODB instead of the DAO shown in the previous
        'ones because DAO does not support the DECIMAL and GUID data types
        Dim con As ADODB.Connection
        Set con = CurrentProject.Connection
        con.Execute "" _
            & "CREATE TABLE [~~Kitsch'n Sync](" _
                & " [Auto]                  COUNTER" _
                & ",[Byte]                  BYTE" _
                & ",[Integer]               SMALLINT" _
                & ",[Long]                  INTEGER" _
                & ",[Single]                REAL" _
                & ",[Double]                FLOAT" _
                & ",[Decimal]               DECIMAL(18,5)" _
                & ",[Currency]              MONEY" _
                & ",[ShortText]             CHAR" _
                & ",[LongText]              MEMO" _
                & ",[PlaceHolder1]          MEMO" _
                & ",[DateTime]              DATETIME" _
                & ",[YesNo]                 BIT" _
                & ",[OleObject]             IMAGE" _
                & ",[ReplicationID]         UNIQUEIDENTIFIER" _
                & ",[Required]              INTEGER NOT NULL" _
                & ",[Unicode Compression]   MEMO WITH COMP" _
                & ",[Indexed]               INTEGER" _
                & ",CONSTRAINT [PrimaryKey] PRIMARY KEY ([Auto])" _
                & ",CONSTRAINT [Unique Index] UNIQUE ([Byte],[Integer],[Long])" _
            & ");"
        con.Execute "CREATE INDEX [Single-Field Index] ON [~~Kitsch'n Sync]([Indexed]);"
        con.Execute "CREATE INDEX [Multi-Field Index] ON [~~Kitsch'n Sync]([Auto],[Required]);"
        con.Execute "CREATE INDEX [IgnoreNulls Index] ON [~~Kitsch'n Sync]([Single],[Double]) WITH IGNORE NULL;"
        con.Execute "CREATE UNIQUE INDEX [Combined Index] ON [~~Kitsch'n Sync]([ShortText],[LongText]) WITH IGNORE NULL;"
        Set con = Nothing
    
        'Add a Hyperlink Field
        Dim AllDefs As DAO.TableDefs, TblDef As DAO.TableDef, Fld As DAO.Field
        Set AllDefs = Application.CurrentDb.TableDefs
        Set TblDef = AllDefs("~~Kitsch'n Sync")
        Set Fld = TblDef.CreateField("Hyperlink", dbMemo)
        Fld.Attributes = dbHyperlinkField + dbVariableField
        Fld.OrdinalPosition = 10
        TblDef.Fields.Append Fld
        
        DoCmd.RunSQL "ALTER TABLE [~~Kitsch'n Sync] DROP COLUMN [PlaceHolder1];"
    End Sub
```
