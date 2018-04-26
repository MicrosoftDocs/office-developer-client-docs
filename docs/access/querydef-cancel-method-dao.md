---
title: "QueryDef.Cancel Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1055470
  
localization_priority: Normal
ms.assetid: 91e61012-c01c-4c24-185c-bdadb7f33a58

---

# QueryDef.Cancel Method (DAO)

## Syntax

 *expression*  . **Cancel**
  
 *expression*  A variable that represents a **QueryDef** object. 
  
## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the  _dbRunAsync_ option). **Cancel** will return a run-time error if  _dbRunAsync_ was not used in the method you're trying to terminate. 
  

