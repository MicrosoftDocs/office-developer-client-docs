---
title: "State Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
f1_keywords:
- ado210.chm1231176
  
localization_priority: Normal
ms.assetid: ade0a50c-e2d8-23ac-4ea9-b012fedcd5db

---

# State Property (ADO)

Indicates for all applicable objects whether the state of the object is open or closed.
  
Indicates for all applicable objects executing an asynchronous method, whether the current state of the object is connecting, executing, or retrieving.
  
## Return Value

Returns a **Long** value that can be an [ObjectStateEnum](objectstateenum.md) value. The default value is **adStateClosed**. 
  
## Remarks

You can use the **State** property to determine the current state of a given object at any time. 
  
The object's **State** property can have a combination of values. For example, if a statement is executing, this property will have a combined value of **adStateOpen** and **adStateExecuting**. 
  
The **State** property is read-only. 
  

