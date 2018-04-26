---
title: "Equivalent ANSI SQL Data Types"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277587
  
localization_priority: Normal
ms.assetid: 720abf59-f9ef-4e14-4223-c873f604ad58
description: "The following table lists ANSI SQL data types, their equivalent Microsoft Access database engine SQL data types, and their valid synonyms. It also lists the equivalent Microsoft® SQL Server™ data types."
---

# Equivalent ANSI SQL Data Types

The following table lists ANSI SQL data types, their equivalent Microsoft Access database engine SQL data types, and their valid synonyms. It also lists the equivalent Microsoft® SQL Server™ data types.
  
|**ANSI SQL data type**|**Microsoft Access SQL data type**|**Synonym**|**Microsoft SQL Server data type**|
|:-----|:-----|:-----|:-----|
|BIT, BIT VARYING  <br/> |BINARY (See Notes)  <br/> |VARBINARY, BINARY VARYING BIT VARYING  <br/> |BINARY, VARBINARY  <br/> |
|Not supported  <br/> |BIT (See Notes)  <br/> |BOOLEAN, LOGICAL, LOGICAL1, YESNO  <br/> |BIT  <br/> |
|Not supported  <br/> |TINYINT  <br/> |INTEGER1, BYTE  <br/> |TINYINT  <br/> |
|Not supported  <br/> |COUNTER (See Notes)  <br/> |AUTOINCREMENT  <br/> |(See Notes)  <br/> |
|Not supported  <br/> |MONEY  <br/> |CURRENCY  <br/> |MONEY  <br/> |
|DATE, TIME, TIMESTAMP  <br/> |DATETIME  <br/> |DATE, TIME (See Notes)  <br/> |DATETIME  <br/> |
|Not supported  <br/> |UNIQUEIDENTIFIER  <br/> |GUID  <br/> |UNIQUEIDENTIFIER  <br/> |
|DECIMAL  <br/> |DECIMAL  <br/> |NUMERIC, DEC  <br/> |DECIMAL  <br/> |
|REAL  <br/> |REAL  <br/> |SINGLE, FLOAT4, IEEESINGLE  <br/> |REAL  <br/> |
|DOUBLE PRECISION, FLOAT  <br/> |FLOAT  <br/> |DOUBLE, FLOAT8, IEEEDOUBLE, NUMBER (See Notes)  <br/> |FLOAT  <br/> |
|SMALLINT  <br/> |SMALLINT  <br/> |SHORT, INTEGER2  <br/> |SMALLINT  <br/> |
|INTEGER  <br/> |INTEGER  <br/> |LONG, INT, INTEGER4  <br/> |INTEGER  <br/> |
|INTERVAL  <br/> |Not supported  <br/> ||Not supported  <br/> |
|Not supported  <br/> |IMAGE  <br/> |LONGBINARY, GENERAL, OLEOBJECT  <br/> |IMAGE  <br/> |
|Not supported  <br/> |TEXT (See Notes)  <br/> |LONGTEXT, LONGCHAR, MEMO, NOTE, NTEXT (See Notes)  <br/> |TEXT  <br/> |
|CHARACTER, CHARACTER VARYING, NATIONAL CHARACTER, NATIONAL CHARACTER VARYING  <br/> |CHAR (See Notes)  <br/> |TEXT(n), ALPHANUMERIC, CHARACTER, STRING, VARCHAR, CHARACTER VARYING, NCHAR, NATIONAL CHARACTER, NATIONAL CHAR, NATIONAL CHARACTER VARYING, NATIONAL CHAR VARYING (See Notes)  <br/> |CHAR, VARCHAR, NCHAR, NVARCHAR  <br/> |
   
> [!NOTE]
>  The ANSI SQL BIT data type does not correspond to the Microsoft Access SQL BIT data type. It corresponds to the BINARY data type instead. There is no ANSI SQL equivalent for the Microsoft Access SQL BIT data type. >  TIMESTAMP is no longer supported as a synonym for DATETIME. >  NUMERIC is no longer supported as a synonym for FLOAT or DOUBLE. NUMERIC is now used as a synonym for DECIMAL. >  A LONGTEXT field is always stored in the Unicode representation format. >  If the data type name TEXT is used without specifying the optional length, for example TEXT(25), a LONGTEXT field is created. This enables [CREATE TABLE statements](create-table-statement-microsoft-access-sql.md) to be written that will yield data types consistent with Microsoft SQL Server. >  A CHAR field is always stored in the Unicode representation format, which is the equivalent of the ANSI SQL NATIONAL CHAR data type. >  If the data type name TEXT is used and the optional length is specified, for example TEXT(25), the data type of the field is equivalent to the CHAR data type. This preserves backwards compatibility for most Microsoft Jet applications, while enabling the TEXT data type (without a length specification) to be aligned with Microsoft SQL Server. 
  

