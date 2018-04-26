---
title: "RecordsetOptionEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3a9d8664-dcb6-cb60-7cf6-e229eb699ef1
description: "Used with the OpenRecordset method to specify characteristics of a new Recordset object."
---

# RecordsetOptionEnum Enumeration (DAO)

Used with the **OpenRecordset** method to specify characteristics of a new **Recordset** object. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbAppendOnly** <br/> |8  <br/> |Allows user to add new records to the dynaset, but prevents user from reading existing records.  <br/> |
|**dbConsistent** <br/> |32  <br/> |Applies updates only to those fields that will not affect other records in the dynaset (dynaset- and snapshot-type only).  <br/> |
|**dbDenyRead** <br/> |2  <br/> |Prevents other users from reading Recordset records (table-type only).  <br/> |
|**dbDenyWrite** <br/> |1  <br/> |Prevents other users from changing Recordset records.  <br/> |
|**dbExecDirect** <br/> |2048  <br/> |Executes the query without first calling the SQLPrepare ODBC function.  <br/> |
|**dbFailOnError** <br/> |128  <br/> |Rolls back updates if an error occurs.  <br/> |
|**dbForwardOnly** <br/> |256  <br/> |Creates a forward-only scrolling snapshot-type Recordset (snapshot-type only).  <br/> |
|**dbInconsistent** <br/> |16  <br/> |Applies updates to all dynaset fields, even if other records are affected (dynaset- and snapshot-type only).  <br/> |
|**dbReadOnly** <br/> |4  <br/> |Opens the Recordset as read-only.  <br/> |
|**dbRunAsync** <br/> |1024  <br/> |Executes the query asynchronously.  <br/> |
|**dbSeeChanges** <br/> |512  <br/> |Generates a run-time error if another user is changing data you are editing (dynaset-type only).  <br/> |
|**dbSQLPassThrough** <br/> |64  <br/> |Sends an SQL statement to an ODBC database (snapshot-type only).  <br/> |
   

