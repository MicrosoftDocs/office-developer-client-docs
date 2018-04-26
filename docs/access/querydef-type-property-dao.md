---
title: "QueryDef.Type Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 03db891d-b958-7cf9-56c1-524d9ff2b9b5

description: "Sets or returns a value that indicates the operational type or data type of an object. Read-onlyInteger ."
---

# QueryDef.Type Property (DAO)

Sets or returns a value that indicates the operational type or data type of an object. Read-only **Integer**. 
  
## Syntax

 *expression*  . **Type**
  
 *expression*  A variable that represents a **QueryDef** object. 
  
## Remarks

For a **QueryDef** object, the possible settings and return values are shown in the following table. 
  
|**Constant**|**Query type**|
|:-----|:-----|
|**dbQAction** <br/> |Action  <br/> |
|**dbQAppend** <br/> |Append  <br/> |
|**dbQCompound** <br/> |Compound  <br/> |
|**dbQCrosstab** <br/> |Crosstab  <br/> |
|**dbQDDL** <br/> |Data-definition  <br/> |
|**dbQDelete** <br/> |Delete  <br/> |
|**dbQMakeTable** <br/> |Make-table  <br/> |
|**dbQProcedure** <br/> |Procedure (ODBCDirect workspaces only)  <br/> > [!NOTE]> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.           |
|**dbQSelect** <br/> |Select  <br/> |
|**dbQSetOperation** <br/> |Union  <br/> |
|**dbQSPTBulk** <br/> |Used with **dbQSQLPassThrough** to specify a query that doesn't return records (Microsoft Access workspaces only).  <br/> |
|**dbQSQLPassThrough** <br/> |Pass-through (Microsoft Access workspaces only)  <br/> |
|**dbQUpdate** <br/> |Update  <br/> |
   
When you append a new **[Field](field-object-dao.md)**, **[Parameter](parameter-object-dao.md)**, or **[Property](property-object-dao.md)** object to the collection of an **[Index](index-object-dao.md)**, **QueryDef**, **[Recordset](recordset-object-dao.md)**, or **[TableDef](tabledef-object-dao.md)** object, an error occurs if the underlying database doesn't support the data type specified for the new object. 
  

