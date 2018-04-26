---
title: "Recordset2.Cancel Method (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: cae49f36-3aad-80d8-c15f-a7a584aa2e9b

---

# Recordset2.Cancel Method (DAO)

## Syntax

 *expression*  . **Cancel**
  
 *expression*  An expression that returns a **Recordset2** object. 
  
## Remarks

Use the **Cancel** method to terminate execution of an asynchronous **Execute** or **OpenConnection** method call (that is, the method was invoked with the  _dbRunAsync_ option). **Cancel** will return a run-time error if  _dbRunAsync_ was not used in the method you're trying to terminate. 
  

