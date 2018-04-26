---
title: "SynchronizeTypeEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f9546171-283d-e9bd-5178-41bd4f41c9a6
description: "Used with the Synchronize method to determine the type of synchronization to apply to two replicas."
---

# SynchronizeTypeEnum Enumeration (DAO)

Used with the **Synchronize** method to determine the type of synchronization to apply to two replicas. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbRepExportChanges** <br/> |1  <br/> |Sends changes from current database to target database.  <br/> |
|**dbRepImpExpChanges** <br/> |4  <br/> |Sends and receives data in a bidirectional exchange.  <br/> |
|**dbRepImportChanges** <br/> |2  <br/> |Receives changes from target database.  <br/> |
|**dbRepSyncInternet** <br/> |16  <br/> |Sends and receives data in a bidirectional exchange.  <br/> |
   

