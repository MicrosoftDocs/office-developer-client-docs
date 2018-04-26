---
title: "UpdateTypeEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 7ac38bae-27fc-f3d0-5b75-569bce547954
description: "Used with the Update method to specify which updates to write to disk."
---

# UpdateTypeEnum Enumeration (DAO)

Used with the **Update** method to specify which updates to write to disk. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbUpdateBatch** <br/> |4  <br/> |All pending changes in the update cache are written to disk.  <br/> |
|**dbUpdateCurrentRecord** <br/> |2  <br/> |Only the current record's pending changes are written to disk.  <br/> |
|**dbUpdateRegular** <br/> |1  <br/> |(Default) Pending changes are not cached and are written to disk immediately.  <br/> |
   

