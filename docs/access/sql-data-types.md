---
title: "SQL Data Types"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277590
  
localization_priority: Normal
ms.assetid: 4fc2dc8c-7825-8fbb-ff91-a0f39ef90115
description: "The Microsoft Access database engine SQL data types consist of 13 primary data types defined by the Microsoft® Jet database engine and several valid synonyms recognized for these data types."
---

# SQL Data Types

The Microsoft Access database engine SQL data types consist of 13 primary data types defined by the Microsoft® Jet database engine and several valid synonyms recognized for these data types.
  
The following table lists the primary data types. The synonyms are identified in [Microsoft Access Database Engine SQL Reserved Words](sql-reserved-words.md).
  
|**Data type**|**Storage size**|**Description**|
|:-----|:-----|:-----|
|BINARY  <br/> |1 byte per character  <br/> |Any type of data may be stored in a field of this type. No translation of the data (for example, to text) is made. How the data is input in a binary field dictates how it will appear as output.  <br/> |
|BIT  <br/> |1 byte  <br/> |Yes and No values and fields that contain only one of two values.  <br/> |
|TINYINT  <br/> |1 byte  <br/> |An integer value between 0 and 255.  <br/> |
|MONEY  <br/> |8 bytes  <br/> |A scaled integer between - 922,337,203,685,477.5808 and 922,337,203,685,477.5807.  <br/> |
|DATETIME (See DOUBLE)  <br/> |8 bytes  <br/> |A date or time value between the years 100 and 9999.  <br/> |
|UNIQUEIDENTIFIER  <br/> |128 bits  <br/> |A unique identification number used with remote procedure calls.  <br/> |
|REAL  <br/> |4 bytes  <br/> |A single-precision floating-point value with a range of - 3.402823E38 to - 1.401298E-45 for negative values, 1.401298E-45 to 3.402823E38 for positive values, and 0.  <br/> |
|FLOAT  <br/> |8 bytes  <br/> |A double-precision floating-point value with a range of - 1.79769313486232E308 to - 4.94065645841247E-324 for negative values, 4.94065645841247E-324 to 1.79769313486232E308 for positive values, and 0.  <br/> |
|SMALLINT  <br/> |2 bytes  <br/> |A short integer between - 32,768 and 32,767. (See Notes)  <br/> |
|INTEGER  <br/> |4 bytes  <br/> |A long integer between - 2,147,483,648 and 2,147,483,647. (See Notes)  <br/> |
|DECIMAL  <br/> |17 bytes  <br/> |An exact numeric data type that holds values from 1028 - 1 through - 1028 - 1. You can define both precision (1 - 28) and scale (0 - defined precision). The default precision and scale are 18 and 0, respectively.  <br/> |
|TEXT  <br/> |2 bytes per character (See Notes)  <br/> |Zero to a maximum of 2.14 gigabytes.  <br/> |
|IMAGE  <br/> |As required  <br/> |Zero to a maximum of 2.14 gigabytes. Used for OLE objects.  <br/> |
|CHARACTER  <br/> |2 bytes per character (See Notes)  <br/> |Zero to 255 characters.  <br/> |
   
> [!NOTE]
>  Both the seed and the increment can be modified using an [ALTER TABLE statement](alter-table-statement-microsoft-access-sql.md). New rows inserted into the table will have values, based on the new seed and increment values, that are automatically generated for the column. If the new seed and increment can yield values that match values generated based on the preceding seed and increment, duplicates will be generated. If the column is a primary key, then inserting new rows may result in errors when duplicate values are generated. >  To find the last value that was used for an auto-increment column, you can use the following statement: SELECT @@IDENTITY. You cannot specify a table name. The value returned is from the last table, containing an auto-increment column, that was updated. 
  

