---
title: SQL Data Types
TOCTitle: SQL Data Types
ms:assetid: 4fc2dc8c-7825-8fbb-ff91-a0f39ef90115
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff193793(v=office.15)
ms:contentKeyID: 48544783
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277590
f1_categories:
- Office.Version=v15
---

# SQL Data Types


_**Applies to:** Access 2013 | Office 2013_

The Microsoft Access database engine SQL data types consist of 13 primary data types defined by the Microsoft® Jet database engine and several valid synonyms recognized for these data types.

The following table lists the primary data types. The synonyms are identified in [Microsoft Access Database Engine SQL Reserved Words](sql-reserved-words.md).

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Data type</p></th>
<th><p>Storage size</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>BINARY</p></td>
<td><p>1 byte per character</p></td>
<td><p>Any type of data may be stored in a field of this type. No translation of the data (for example, to text) is made. How the data is input in a binary field dictates how it will appear as output.</p></td>
</tr>
<tr class="even">
<td><p>BIT</p></td>
<td><p>1 byte</p></td>
<td><p>Yes and No values and fields that contain only one of two values.</p></td>
</tr>
<tr class="odd">
<td><p>TINYINT</p></td>
<td><p>1 byte</p></td>
<td><p>An integer value between 0 and 255.</p></td>
</tr>
<tr class="even">
<td><p>MONEY</p></td>
<td><p>8 bytes</p></td>
<td><p>A scaled integer between – 922,337,203,685,477.5808 and 922,337,203,685,477.5807.</p></td>
</tr>
<tr class="odd">
<td><p>DATETIME (See DOUBLE)</p></td>
<td><p>8 bytes</p></td>
<td><p>A date or time value between the years 100 and 9999.</p></td>
</tr>
<tr class="even">
<td><p>UNIQUEIDENTIFIER</p></td>
<td><p>128 bits</p></td>
<td><p>A unique identification number used with remote procedure calls.</p></td>
</tr>
<tr class="odd">
<td><p>REAL</p></td>
<td><p>4 bytes</p></td>
<td><p>A single-precision floating-point value with a range of – 3.402823E38 to – 1.401298E-45 for negative values, 1.401298E-45 to 3.402823E38 for positive values, and 0.</p></td>
</tr>
<tr class="even">
<td><p>FLOAT</p></td>
<td><p>8 bytes</p></td>
<td><p>A double-precision floating-point value with a range of – 1.79769313486232E308 to – 4.94065645841247E-324 for negative values, 4.94065645841247E-324 to 1.79769313486232E308 for positive values, and 0.</p></td>
</tr>
<tr class="odd">
<td><p>SMALLINT</p></td>
<td><p>2 bytes</p></td>
<td><p>A short integer between – 32,768 and 32,767. (See Notes)</p></td>
</tr>
<tr class="even">
<td><p>INTEGER</p></td>
<td><p>4 bytes</p></td>
<td><p>A long integer between – 2,147,483,648 and 2,147,483,647. (See Notes)</p></td>
</tr>
<tr class="odd">
<td><p>DECIMAL</p></td>
<td><p>17 bytes</p></td>
<td><p>An exact numeric data type that holds values from 1028 - 1 through - 1028 - 1. You can define both precision (1 - 28) and scale (0 - defined precision). The default precision and scale are 18 and 0, respectively.</p></td>
</tr>
<tr class="even">
<td><p>TEXT</p></td>
<td><p>2 bytes per character (See Notes)</p></td>
<td><p>Zero to a maximum of 2.14 gigabytes.</p></td>
</tr>
<tr class="odd">
<td><p>IMAGE</p></td>
<td><p>As required</p></td>
<td><p>Zero to a maximum of 2.14 gigabytes. Used for OLE objects.</p></td>
</tr>
<tr class="even">
<td><p>CHARACTER</p></td>
<td><p>2 bytes per character (See Notes)</p></td>
<td><p>Zero to 255 characters.</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <UL>
> <LI>
> <P>Both the seed and the increment can be modified using an <A href="alter-table-statement-microsoft-access-sql.md">ALTER TABLE statement</A>. New rows inserted into the table will have values, based on the new seed and increment values, that are automatically generated for the column. If the new seed and increment can yield values that match values generated based on the preceding seed and increment, duplicates will be generated. If the column is a primary key, then inserting new rows may result in errors when duplicate values are generated.</P>
> <LI>
> <P>To find the last value that was used for an auto-increment column, you can use the following statement: SELECT @@IDENTITY. You cannot specify a table name. The value returned is from the last table, containing an auto-increment column, that was updated.</P></LI></UL>


