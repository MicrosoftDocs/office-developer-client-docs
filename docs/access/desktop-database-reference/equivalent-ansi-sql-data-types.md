---
title: Equivalent ANSI SQL data types
TOCTitle: Equivalent ANSI SQL data types
ms:assetid: 720abf59-f9ef-4e14-4223-c873f604ad58
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195814(v=office.15)
ms:contentKeyID: 48545599
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277587
f1_categories:
- Office.Version=v15
localization_priority: Priority
---

# Equivalent ANSI SQL data types


**Applies to**: Access 2013, Office 2013

The following table lists ANSI SQL data types, their equivalent Microsoft Access database engine SQL data types, and their valid synonyms. It also lists the equivalent Microsoft SQL Server™ data types.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>ANSI SQL data type</p></th>
<th><p>Microsoft Access SQL data type</p></th>
<th><p>Synonym</p></th>
<th><p>Microsoft SQL Server data type</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BIT, BIT VARYING</p></td>
<td><p>BINARY (See Notes)</p></td>
<td><p>VARBINARY, BINARY VARYING BIT VARYING</p></td>
<td><p>BINARY, VARBINARY</p></td>
</tr>
<tr class="even">
<td><p>Not supported</p></td>
<td><p>BIT (See Notes)</p></td>
<td><p>BOOLEAN, LOGICAL, LOGICAL1, YESNO</p></td>
<td><p>BIT</p></td>
</tr>
<tr class="odd">
<td><p>Not supported</p></td>
<td><p>TINYINT</p></td>
<td><p>INTEGER1, BYTE</p></td>
<td><p>TINYINT</p></td>
</tr>
<tr class="even">
<td><p>Not supported</p></td>
<td><p>COUNTER (See Notes)</p></td>
<td><p>AUTOINCREMENT</p></td>
<td><p>(See Notes)</p></td>
</tr>
<tr class="odd">
<td><p>Not supported</p></td>
<td><p>MONEY</p></td>
<td><p>CURRENCY</p></td>
<td><p>MONEY</p></td>
</tr>
<tr class="even">
<td><p>DATE, TIME, TIMESTAMP</p></td>
<td><p>DATETIME</p></td>
<td><p>DATE, TIME (See Notes)</p></td>
<td><p>DATETIME</p></td>
</tr>
<tr class="odd">
<td><p>Not supported</p></td>
<td><p>UNIQUEIDENTIFIER</p></td>
<td><p>GUID</p></td>
<td><p>UNIQUEIDENTIFIER</p></td>
</tr>
<tr class="even">
<td><p>DECIMAL</p></td>
<td><p>DECIMAL</p></td>
<td><p>NUMERIC, DEC</p></td>
<td><p>DECIMAL</p></td>
</tr>
<tr class="odd">
<td><p>REAL</p></td>
<td><p>REAL</p></td>
<td><p>SINGLE, FLOAT4, IEEESINGLE</p></td>
<td><p>REAL</p></td>
</tr>
<tr class="even">
<td><p>DOUBLE PRECISION, FLOAT</p></td>
<td><p>FLOAT</p></td>
<td><p>DOUBLE, FLOAT8, IEEEDOUBLE, NUMBER (See Notes)</p></td>
<td><p>FLOAT</p></td>
</tr>
<tr class="odd">
<td><p>SMALLINT</p></td>
<td><p>SMALLINT</p></td>
<td><p>SHORT, INTEGER2</p></td>
<td><p>SMALLINT</p></td>
</tr>
<tr class="even">
<td><p>INTEGER</p></td>
<td><p>INTEGER</p></td>
<td><p>LONG, INT, INTEGER4</p></td>
<td><p>INTEGER</p></td>
</tr>
<tr class="odd">
<td><p>INTERVAL</p></td>
<td><p>Not supported</p></td>
<td><p></p></td>
<td><p>Not supported</p></td>
</tr>
<tr class="even">
<td><p>Not supported</p></td>
<td><p>IMAGE</p></td>
<td><p>LONGBINARY, GENERAL, OLEOBJECT</p></td>
<td><p>IMAGE</p></td>
</tr>
<tr class="odd">
<td><p>Not supported</p></td>
<td><p>TEXT (See Notes)</p></td>
<td><p>LONGTEXT, LONGCHAR, MEMO, NOTE, NTEXT (See Notes)</p></td>
<td><p>TEXT</p></td>
</tr>
<tr class="even">
<td><p>CHARACTER, CHARACTER VARYING, NATIONAL CHARACTER, NATIONAL CHARACTER VARYING</p></td>
<td><p>CHAR (See Notes)</p></td>
<td><p>TEXT(n), ALPHANUMERIC, CHARACTER, STRING, VARCHAR, CHARACTER VARYING, NCHAR, NATIONAL CHARACTER, NATIONAL CHAR, NATIONAL CHARACTER VARYING, NATIONAL CHAR VARYING (See Notes)</p></td>
<td><p>CHAR, VARCHAR, NCHAR, NVARCHAR</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> - The ANSI SQL BIT data type does not correspond to the Microsoft Access SQL BIT data type. It corresponds to the BINARY data type instead. There is no ANSI SQL equivalent for the Microsoft Access SQL BIT data type.
> - TIMESTAMP is no longer supported as a synonym for DATETIME.
> - NUMERIC is no longer supported as a synonym for FLOAT or DOUBLE. NUMERIC is now used as a synonym for DECIMAL.
> - A LONGTEXT field is always stored in the Unicode representation format.
> - If the data type name TEXT is used without specifying the optional length, for example TEXT(25), a LONGTEXT field is created. This enables [CREATE TABLE statements](create-table-statement-microsoft-access-sql.md) to be written that will yield data types consistent with Microsoft SQL Server.
> - A CHAR field is always stored in the Unicode representation format, which is the equivalent of the ANSI SQL NATIONAL CHAR data type.
> - If the data type name TEXT is used and the optional length is specified, for example TEXT(25), the data type of the field is equivalent to the CHAR data type. This preserves backwards compatibility for most Microsoft Jet applications, while enabling the TEXT data type (without a length specification) to be aligned with Microsoft SQL Server.


