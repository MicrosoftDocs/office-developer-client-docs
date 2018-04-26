---
title: "QueryDef.OpenRecordset Method (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b4908c36-c156-e269-e2ad-b1fa20ec4884

description: "Creates a new Recordset object and appends it to the Recordsets collection."
---

# QueryDef.OpenRecordset Method (DAO)

Creates a new **[Recordset](recordset-object-dao.md)** object and appends it to the **Recordsets** collection. 
  
## Syntax

 *expression*  . **OpenRecordset**( ** *Type* **, ** *Options* **, ** *LockEdit* ** ) 
  
 *expression*  A variable that represents a **QueryDef** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Type_ <br/> |Optional  <br/> |**Variant** <br/> |A **[RecordsetTypeEnum](recordsettypeenum-enumeration-dao.md)** constant that indicates the type of **Recordset** to open.  <br/> > [!NOTE]> If you open a **Recordset** in a Microsoft Access workspace and you don't specify a type, **OpenRecordset** creates a table-type **Recordset**, if possible. If you specify a linked table or query, **OpenRecordset** creates a dynaset-type **Recordset**.           |
| _Options_ <br/> |Optional  <br/> |**Variant** <br/> |A combination of **[RecordsetOptionEnum](recordsetoptionenum-enumeration-dao.md)** constants that specify characteristics of the new **Recordset**.  <br/> > [!NOTE]> The constants **dbConsistent** and **dbInconsistent** are mutually exclusive, and using both causes an error. Supplying a lockedits argument when options uses the **dbReadOnly** constant also causes an error.           |
| _LockEdit_ <br/> |Optional  <br/> |**Variant** <br/> |A **[LockTypeEnum](locktypeenum-enumeration-dao.md)** constant that determines the locking for the **Recordset**.  <br/> > [!NOTE]> You can use **dbReadOnly** in either the options argument or the lockedits argument, but not both. If you use it for both arguments, a run-time error occurs.           |
   
### Return Value

Recordset
  
## Remarks

You should also use the **[dbSeeChanges](recordsetoptionenum-enumeration-dao.md)** constant if you open a **Recordset** in a Microsoft Access database engine-connected ODBC workspace against a Microsoft SQL Server 6.0 (or later) table that has an IDENTITY column, otherwise an error may result. 
  
Opening more than one **Recordset** on an ODBC data source may fail because the connection is busy with a prior **OpenRecordset** call. One way around this is to fully populate the **Recordset** by using the **[MoveLast](recordset-movelast-method-dao.md)** method as soon as the **Recordset** is opened. 
  
Closing a **Recordset** with the **Close** method automatically deletes it from the **Recordsets** collection. 
  
> [!NOTE]
> If  *source*  refers to an SQL statement composed of a string concatenated with a non-integer value, and the system parameters specify a non-U.S. decimal character such as a comma (for example,  `strSQL = "PRICE > " &amp; lngPrice`, and  `lngPrice = 125,50`), an error occurs when you try to open the **Recordset**. This is because during concatenation, the number will be converted to a string using your system's default decimal character, and SQL only accepts U.S. decimal characters. 
  

