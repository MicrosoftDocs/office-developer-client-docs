---
title: "LockTypeEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d40f984c-b37f-72f7-7b05-752f106b6029

description: "Specifies the type of record locking used when opening a recordset."
---

# LockTypeEnum Enumeration (DAO)

Specifies the type of record locking used when opening a recordset.
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbOptimistic** <br/> |3  <br/> |Optimistic concurrency based on record ID. Cursor compares record ID in old and new records to determine if changes have been made since the record was last accessed.  <br/> |
|**dbOptimisticBatch** <br/> |5  <br/> |Enables batch optimistic updates (ODBCDirect workspaces only).  <br/> |
|**dbOptimisticValue** <br/> |1  <br/> |Optimistic concurrency based on record values. Cursor compares data values in old and new records to determine if changes have been made since the record was last accessed (ODBCDirect workspaces only).  <br/> > [!NOTE]> ODBCDirect workspaces are not supported in Microsoft Access 2013. Use ADO if you want to access external data sources without using the Microsoft Access database engine.           |
|**dbPessimistic** <br/> |2  <br/> |Pessimistic concurrency. Cursor uses the lowest level of locking sufficient to ensure that the record can be updated.  <br/> |
   

