---
title: "Field2.Type Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 057d6ec9-b72c-cee6-005a-6d916e3dda29
description: "Sets or returns a value that indicates the operational type or data type of an object. Read/write Integer ."
---

# Field2.Type Property (DAO)

Sets or returns a value that indicates the operational type or data type of an object. Read/write **Integer**. 
  
## Syntax

 *expression*  . **Type**
  
 *expression*  A variable that represents a **Field2** object. 
  
## Remarks

The setting or return value is a constant that indicates an operational or data type. For a **Field2** object, this property is read/write until the object is appended to a collection or to another object, after which it's read-only. 
  
For a **Field2** object, the possible settings and return values are described in the following table. 
  
|**Constant**|**Description**|
|:-----|:-----|
|**dbBigInt** <br/> |Big Integer  <br/> |
|**dbBinary** <br/> |Binary  <br/> |
|**dbBoolean** <br/> |Boolean  <br/> |
|**dbByte** <br/> |Byte  <br/> |
|**dbChar** <br/> |Char  <br/> |
|**dbCurrency** <br/> |Currency  <br/> |
|**dbDate** <br/> |Date/Time  <br/> |
|**dbDecimal** <br/> |Decimal  <br/> |
|**dbDouble** <br/> |Double  <br/> |
|**dbFloat** <br/> |Float  <br/> |
|**dbGUID** <br/> |GUID  <br/> |
|**dbInteger** <br/> |Integer  <br/> |
|**dbLong** <br/> |Long  <br/> |
|**dbLongBinary** <br/> |Long Binary (OLE Object)  <br/> |
|**dbMemo** <br/> |Memo  <br/> |
|**dbNumeric** <br/> |Numeric  <br/> |
|**dbSingle** <br/> |Single  <br/> |
|**dbText** <br/> |Text  <br/> |
|**dbTime** <br/> |Time  <br/> |
|**dbTimeStamp** <br/> |Time Stamp  <br/> |
|**dbVarBinary** <br/> |VarBinary  <br/> |
   
When you append a new **Field2**, **Parameter**, or **Property** object to the collection of an **Index**, **QueryDef**, **Recordset**, or **TableDef** object, an error occurs if the underlying database doesn't support the data type specified for the new object. 
  

