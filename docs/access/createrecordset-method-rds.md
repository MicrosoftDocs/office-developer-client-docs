---
title: "CreateRecordset Method (RDS)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 19524509-31da-9af1-4062-cd3c59b51278
---

# CreateRecordset Method (RDS)

Creates an empty, disconnected [Recordset](recordset-object-ado.md).
  
## Syntax

 *object*  . **CreateRecordset**( *ColumnInfos*  ) 
  
## Parameters

-  *Object* 
    
- An object variable that represents an [RDSServer.DataFactory](datafactory-object-rdsserver.md) or [RDS.DataControl](datacontrol-object-rds.md) object. 
    
-  *ColumnsInfos* 
    
- A **Variant** array of attributes that defines each column in the **Recordset** created. Each column definition contains an array of four required attributes and one optional attribute. The set of column arrays is then grouped into an array, which defines the **Recordset**. 
    
|**Attribute**|**Description**|
|:-----|:-----|
|Name  <br/> |Name of the column header.  <br/> |
|Type  <br/> |Integer of the data type.  <br/> |
|Size  <br/> |Integer of the width in characters, regardless of data type.  <br/> |
|Nullability  <br/> |Boolean value.  <br/> |
|Scale           (Optional)  <br/> |This optional attribute defines the scale for numeric fields. If this value is not specified, numeric values will be truncated to a scale of three. Precision is not affected, but the number of digits following the decimal point will be truncated to three.  <br/> |
   
## Remarks

The server-side business object can populate the resulting **Recordset** with data from a non-OLE DB data provider, such as an operating system file containing stock quotes. 
  
The following table lists the [DataTypeEnum](datatypeenum.md) values supported by the **CreateRecordset** method. The number listed is the reference number used to define fields. 
  
Each of the data types is either fixed length or variable length. Fixed-length types should be defined with a size of -1, because the size is predetermined and a size definition is still required. Variable-length data types allow a size from 1 to 32767.
  
For some of the variable data types, the type may be coerced to the type noted in the Substitution column. You won't see the substitutions until after the **Recordset** is created and filled. Then you can check for the actual data type, if necessary. 
  
|**Length**|**Constant**|**Number**|**Substitution**|
|:-----|:-----|:-----|:-----|
|Fixed  <br/> |**adTinyInt** <br/> |16  <br/> ||
|Fixed  <br/> |**adSmallInt** <br/> |2  <br/> ||
|Fixed  <br/> |**adInteger** <br/> |3  <br/> ||
|Fixed  <br/> |**adBigInt** <br/> |20  <br/> ||
|Fixed  <br/> |**adUnsignedTinyInt** <br/> |17  <br/> ||
|Fixed  <br/> |**adUnsignedSmallInt** <br/> |18  <br/> ||
|Fixed  <br/> |**adUnsignedInt** <br/> |19  <br/> ||
|Fixed  <br/> |**adUnsignedBigInt** <br/> |21  <br/> ||
|Fixed  <br/> |**adSingle** <br/> |4  <br/> ||
|Fixed  <br/> |**adDouble** <br/> |5  <br/> ||
|Fixed  <br/> |**adCurrency** <br/> |6  <br/> ||
|Fixed  <br/> |**adDecimal** <br/> |14  <br/> ||
|Fixed  <br/> |**adNumeric** <br/> |131  <br/> ||
|Fixed  <br/> |**adBoolean** <br/> |11  <br/> ||
|Fixed  <br/> |**adError** <br/> |10  <br/> ||
|Fixed  <br/> |**adGuid** <br/> |72  <br/> ||
|Fixed  <br/> |**adDate** <br/> |7  <br/> ||
|Fixed  <br/> |**adDBDate** <br/> |133  <br/> ||
|Fixed  <br/> |**adDBTime** <br/> |134  <br/> ||
|Fixed  <br/> |**adDBTimestamp** <br/> |135  <br/> |7  <br/> |
|Variable  <br/> |**adBSTR** <br/> |8  <br/> |130  <br/> |
|Variable  <br/> |**adChar** <br/> |129  <br/> |200  <br/> |
|Variable  <br/> |**adVarChar** <br/> |200  <br/> ||
|Variable  <br/> |**adLongVarChar** <br/> |201  <br/> |200  <br/> |
|Variable  <br/> |**adWChar** <br/> |130  <br/> ||
|Variable  <br/> |**adVarWChar** <br/> |202  <br/> |130  <br/> |
|Variable  <br/> |**adLongVarWChar** <br/> |203  <br/> |130  <br/> |
|Variable  <br/> |**adBinary** <br/> |128  <br/> ||
|Variable  <br/> |**adVarBinary** <br/> |204  <br/> ||
|Variable  <br/> |**adLongVarBinary** <br/> |205  <br/> |204  <br/> |
   

