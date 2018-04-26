---
title: "ODBC Scalar Functions"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277473
  
localization_priority: Normal
ms.assetid: dc1096bf-8241-036a-14c6-b19afae45454
description: "Microsoft® Access SQL supports the use of the ODBC defined syntax for scalar functions. For example, the query:"
---

# ODBC Scalar Functions

Microsoft® Access SQL supports the use of the ODBC defined syntax for scalar functions. For example, the query:
  
SELECT DAILYCLOSE, DAILYCHANGE FROM DAILYQUOTE WHERE {fn ABS(DAILYCHANGE)} \> 5
  
Would return all rows where the absolute value of the change in the price of a stock was greater than five.
  
A subset of the ODBC defined scalar functions is supported. The following table lists the functions that are supported.
  
For a description of the arguments and a complete explanation of the escape syntax for including functions in a SQL statement, see the ODBC documentation.
  
## String Functions

||||
|:-----|:-----|:-----|
|ASCII  <br/> |LENGTH  <br/> |RTRIM  <br/> |
|CHAR  <br/> |LOCATE  <br/> |SPACE  <br/> |
|CONCAT  <br/> |LTRIM  <br/> |SUBSTRING  <br/> |
|LCASE  <br/> |RIGHT  <br/> |UCASE  <br/> |
|LEFT  <br/> |||
   
## Numeric Functions

||||
|:-----|:-----|:-----|
|ABS  <br/> |FLOOR  <br/> |SIN  <br/> |
|ATAN  <br/> |LOG  <br/> |SQRT  <br/> |
|CEILING  <br/> |POWER  <br/> |TAN  <br/> |
|COS  <br/> |RAND  <br/> |MOD  <br/> |
|EXP  <br/> |SIGN  <br/> ||
   
## Time &amp; Date Functions

||||
|:-----|:-----|:-----|
|CURDATE  <br/> |DAYOFYEAR  <br/> |MONTH  <br/> |
|CURTIME  <br/> |YEAR  <br/> |WEEK  <br/> |
|NOW  <br/> |HOUR  <br/> |QUARTER  <br/> |
|DAYOFMONTH  <br/> |MINUTE  <br/> |MONTHNAME  <br/> |
|DAYOFWEEK  <br/> |SECOND  <br/> |DAYNAME  <br/> |
   
## Data Type Conversion

|||
|:-----|:-----|
|CONVERT  <br/> |String literals can be converted to the following data types: SQL_FLOAT, SQL_DOUBLE, SQL_NUMERIC, SQL_INTEGER, SQL_REAL, SQL_SMALLINT, SQL_VARCHAR and SQL_DATETIME.  <br/> |
   

