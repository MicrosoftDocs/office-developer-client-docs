---
title: "RecordStatusEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: bf4492f2-8d8f-f10f-7a3c-d6296d2ce96b
description: "Used with the RecordStatus property to indicate the update status of the current record if it is part of a batch update."
---

# RecordStatusEnum Enumeration (DAO)

Used with the **RecordStatus** property to indicate the update status of the current record if it is part of a batch update. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbRecordDBDeleted** <br/> |4  <br/> |The record has been deleted locally and in the database.  <br/> |
|**dbRecordDeleted** <br/> |3  <br/> |The record has been deleted, but not yet deleted in the database.  <br/> |
|**dbRecordModified** <br/> |1  <br/> |The record has been modified and not updated in the database.  <br/> |
|**dbRecordNew** <br/> |2  <br/> |The record has been inserted with the **AddNew** method, but not yet inserted into the database.  <br/> |
|**dbRecordUnmodified** <br/> |0  <br/> |(Default) The record has not been modified or has been updated successfully.  <br/> |
   

