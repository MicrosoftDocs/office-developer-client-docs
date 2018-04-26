---
title: "UpdateCriteriaEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 1f83a0c6-bdc8-9c3e-380b-524f611f6476
description: "Used with the UpdateOptions method to specify how a batch update is constructed."
---

# UpdateCriteriaEnum Enumeration (DAO)

Used with the **UpdateOptions** method to specify how a batch update is constructed. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbCriteriaAllCols** <br/> |4  <br/> |Uses the key column(s) and all the columns in the where clause.  <br/> |
|**dbCriteriaDeleteInsert** <br/> |16  <br/> |Uses a pair of DELETE and INSERT statements for each modified row.  <br/> |
|**dbCriteriaKey** <br/> |1  <br/> |Uses just the key column(s) in the where clause.  <br/> |
|**dbCriteriaModValues** <br/> |2  <br/> |Uses the key column(s) and all updated columns in the where clause.  <br/> |
|**dbCriteriaTimestamp** <br/> |8  <br/> |Uses just the timestamp column if available (will generate a run-time error if no timestamp column is in the result set).  <br/> |
|**dbCriteriaUpdate** <br/> |32  <br/> |Uses an UPDATE statement for each modified row.  <br/> |
   

