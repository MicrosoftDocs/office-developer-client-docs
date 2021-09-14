---
title: Field.Type property (DAO)
TOCTitle: Type Property
description: Type property
ms:assetid: 1295ca40-78c1-bdd0-d407-e1b5be8adfd4
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845405(v=office.15)
ms:contentKeyID: 48543345
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Priority
---

# Field.Type property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns a value that indicates the operational type or data type of an object. Read/write **Integer**.

## Syntax

*expression* .Type

*expression* A variable that represents a **Field** object.

## Remarks

The setting or return value is a constant that indicates an operational or data type. For a **Field** object, this property is read/write until the object is appended to a collection or to another object, after which it's read-only.

For a **Field** object, the possible settings and return values are described in the following table.

|**Constant**|**Value**|**Description**|
|:----------|:----------|:----------|
|**dbBigInt**|16|Big Integer|
|**dbBinary**|9|Binary|
|**dbBoolean**|1|Boolean|
|**dbByte**|2|Byte|
|**dbChar**|18|Char|
|**dbCurrency**|5|Currency|
|**dbDate**|8|Date/Time|
|**dbDecimal**|20|Decimal|
|**dbDouble**|7|Double|
|**dbFloat**|21|Float|
|**dbGUID**|15|GUID|
|**dbInteger**|3|Integer|
|**dbLong**|4|Long|
|**dbLongBinary**|11|Long Binary (OLE Object)|
|**dbMemo**|12|Memo|
|**dbNumeric**|19|Numeric|
|**dbSingle**|6|Single|
|**dbText**|10|Text|
|**dbTime**|22|Time|
|**dbTimeStamp**|23|Time Stamp|
|**dbVarBinary**|17|VarBinary|

When you append a new **Field**, **Parameter**, or **Property** object to the collection of an **[Index](index-object-dao.md)**, **QueryDef**, **Recordset**, or **TableDef** object, an error occurs if the underlying database doesn't support the data type specified for the new object.
