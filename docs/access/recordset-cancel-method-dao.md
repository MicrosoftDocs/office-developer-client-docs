---
title: "Recordset.Cancel Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 89acfbf1-b937-dc19-ada1-6f8f50489147

---

# Recordset.Cancel Method (DAO)

## Syntax

 *expression*  . **Cancel**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the  _dbRunAsync_ option). **Cancel** will return a run-time error if  _dbRunAsync_ was not used in the method you're trying to terminate. 
  

