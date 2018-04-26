---
title: "QueryDef.Close Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1052976
  
localization_priority: Normal
ms.assetid: b2b63462-453d-9e2b-0bb3-69a4a7a6ecef
description: "Closes an open QueryDef ."
---

# QueryDef.Close Method (DAO)

Closes an open **QueryDef**. 
  
## Syntax

 *expression*  . **Close**
  
 *expression*  A variable that represents a **QueryDef** object. 
  
## Remarks

If the **QueryDef** object is already closed when you use **Close**, a run-time error occurs. 
  
An alternative to the **Close** method is to set the value of an object variable to **Nothing** (  `Set dbsTemp = Nothing`).
  

