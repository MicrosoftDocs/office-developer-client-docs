---
title: "Aggregate Functions, the CALC Function, and the NEW Keyword"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: c91fef19-bf41-8d04-f195-5470fb18393f
description: "Data shaping supports the following functions. The name assigned to the chapter containing the column to be operated on is the chapter-alias ."
---

# Aggregate Functions, the CALC Function, and the NEW Keyword

Data shaping supports the following functions. The name assigned to the chapter containing the column to be operated on is the  *chapter-alias*  . 
  
A chapter-alias may be fully qualified, consisting of each chapter column name leading to the chapter containing the  *column-name,*  all separated by periods. For example, if the parent chapter, chap1, contains a child chapter, chap2, that has an amount column, amt, then the qualified name would be chap1.chap2.amt. 
  
|**Aggregate Functions**|**Description**|
|:-----|:-----|
|SUM( *chapter-alias*  .  *column-name*  )  <br/> |Calculates the sum of all values in the specified column.  <br/> |
|AVG( *chapter-alias*  .  *column-name*  )  <br/> |Calculates the average of all values in the specified column.  <br/> |
|MAX( *chapter-alias*  .  *column-name*  )  <br/> |Calculates the maximum value in the specified column.  <br/> |
|MIN( *chapter-alias*  .  *column-name*  )  <br/> |Calculates the minimum value in the specified column.  <br/> |
|COUNT( *chapter-alias*  [.  *column-name*  ])  <br/> |Counts the number of rows in the specified alias. If a column is specified, only rows for which that column is non-Null are included in the count.  <br/> |
|STDEV( *chapter-alias*  .  *column-name*  )  <br/> |Calculates the standard deviation in the specified column.  <br/> |
|ANY( *chapter-alias*  .  *column-name*  )  <br/> |A value of the specified column. ANY has a predictable value only when the value of the column is the same for all rows in the chapter.  <br/> > [!NOTE]> If the column does not contain the same value for all of the rows in the chapter, the SHAPE command arbitrarily returns one of the values to be the value of the ANY function.           |
   
|**Calculated expression**|**Description**|
|:-----|:-----|
|CALC( *expression*  )  <br/> |Calculates an arbitrary expression, but only on the row of the **Recordset** containing the CALC function. Any expression using these [Visual Basic for Applications (VBA) Functions](visual-basic-for-applications-functions.md) is allowed.  <br/> |
   
|**NEW keyword**|**Description**|
|:-----|:-----|
|NEW  *field-type*  [(  *width*  |  *scale*  |  *precision*  |  *error*  [,  *scale*  |  *error*  ])]  <br/> |Adds an empty column of the specified type to the **Recordset**.  <br/> |
   
The  *field-type*  passed with the NEW keyword can be any of the following data types. 
  
|**OLE DB data types**|**ADO data type equivalent(s)**|
|:-----|:-----|
|DBTYPE_BSTR  <br/> |adBSTR  <br/> |
|DBTYPE_BOOL  <br/> |adBoolean  <br/> |
|DBTYPE_DECIMAL  <br/> |adDecimal  <br/> |
|DBTYPE_UI1  <br/> |adUnsignedTinyInt  <br/> |
|DBTYPE_I1  <br/> |adTinyInt  <br/> |
|DBTYPE_UI2  <br/> |adUnsignedSmallInt  <br/> |
|DBTYPE_UI4  <br/> |adUnsignedInt  <br/> |
|DBTYPE_I8  <br/> |adBigInt  <br/> |
|DBTYPE_UI8  <br/> |adUnsignedBigInt  <br/> |
|DBTYPE_GUID  <br/> |adGuid  <br/> |
|DBTYPE_BYTES  <br/> |adBinary, AdVarBinary, adLongVarBinary  <br/> |
|DBTYPE_STR  <br/> |adChar, adVarChar, adLongVarChar  <br/> |
|DBTYPE_WSTR  <br/> |adWChar, adVarWChar, adLongVarWChar  <br/> |
|DBTYPE_NUMERIC  <br/> |adNumeric  <br/> |
|DBTYPE_DBDATE  <br/> |adDBDate  <br/> |
|DBTYPE_DBTIME  <br/> |adDBTime  <br/> |
|DBTYPE_DBTIMESTAMP  <br/> |adDBTimeStamp  <br/> |
|DBTYPE_VARNUMERIC  <br/> |adVarNumeric  <br/> |
|DBTYPE_FILETIME  <br/> |adFileTime  <br/> |
|DBTYPE_ERROR  <br/> |adError  <br/> |
   
When the new field is of type decimal (in OLE DB, DBTYPE_DECIMAL, or in ADO, adDecimal), you must specify the precision and scale values.
  

