---
title: ODBC Scalar Functions
TOCTitle: ODBC Scalar Functions
ms:assetid: dc1096bf-8241-036a-14c6-b19afae45454
ms:mtpsurl: https://msdn.microsoft.com/library/Ff835353(v=office.15)
ms:contentKeyID: 48548120
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277473
f1_categories:
- Office.Version=v15
---

# ODBC Scalar Functions


**Applies to**: Access 2013, Office 2013

Microsoft Access SQL supports the use of the ODBC defined syntax for scalar functions. For example, the query:

SELECT DAILYCLOSE, DAILYCHANGE FROM DAILYQUOTE WHERE {fn ABS(DAILYCHANGE)} \> 5

Would return all rows where the absolute value of the change in the price of a stock was greater than five.

A subset of the ODBC defined scalar functions is supported. The following table lists the functions that are supported.

For a description of the arguments and a complete explanation of the escape syntax for including functions in a SQL statement, see the ODBC documentation.

## String Functions

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>ASCII</p></td>
<td><p>LENGTH</p></td>
<td><p>RTRIM</p></td>
</tr>
<tr class="even">
<td><p>CHAR</p></td>
<td><p>LOCATE</p></td>
<td><p>SPACE</p></td>
</tr>
<tr class="odd">
<td><p>CONCAT</p></td>
<td><p>LTRIM</p></td>
<td><p>SUBSTRING</p></td>
</tr>
<tr class="even">
<td><p>LCASE</p></td>
<td><p>RIGHT</p></td>
<td><p>UCASE</p></td>
</tr>
<tr class="odd">
<td><p>LEFT</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Numeric Functions

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>ABS</p></td>
<td><p>FLOOR</p></td>
<td><p>SIN</p></td>
</tr>
<tr class="even">
<td><p>ATAN</p></td>
<td><p>LOG</p></td>
<td><p>SQRT</p></td>
</tr>
<tr class="odd">
<td><p>CEILING</p></td>
<td><p>POWER</p></td>
<td><p>TAN</p></td>
</tr>
<tr class="even">
<td><p>COS</p></td>
<td><p>RAND</p></td>
<td><p>MOD</p></td>
</tr>
<tr class="odd">
<td><p>EXP</p></td>
<td><p>SIGN</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Time & Date Functions

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>CURDATE</p></td>
<td><p>DAYOFYEAR</p></td>
<td><p>MONTH</p></td>
</tr>
<tr class="even">
<td><p>CURTIME</p></td>
<td><p>YEAR</p></td>
<td><p>WEEK</p></td>
</tr>
<tr class="odd">
<td><p>NOW</p></td>
<td><p>HOUR</p></td>
<td><p>QUARTER</p></td>
</tr>
<tr class="even">
<td><p>DAYOFMONTH</p></td>
<td><p>MINUTE</p></td>
<td><p>MONTHNAME</p></td>
</tr>
<tr class="odd">
<td><p>DAYOFWEEK</p></td>
<td><p>SECOND</p></td>
<td><p>DAYNAME</p></td>
</tr>
</tbody>
</table>


## Data Type Conversion

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>CONVERT</p></td>
<td><p>String literals can be converted to the following data types: SQL_FLOAT, SQL_DOUBLE, SQL_NUMERIC, SQL_INTEGER, SQL_REAL, SQL_SMALLINT, SQL_VARCHAR and SQL_DATETIME.</p></td>
</tr>
</tbody>
</table>

