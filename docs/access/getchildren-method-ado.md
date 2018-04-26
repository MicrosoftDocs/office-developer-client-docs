---
title: "GetChildren Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 998cf640-ffc7-51e1-4d1e-4797f7cdea4a

---

# GetChildren Method (ADO)

Returns a [Recordset](recordset-object-ado.md) whose rows represent the children of a collection [Record](record-object-ado.md).
  
## Syntax

 **Set** * recordset *  =  *record*  . **GetChildren**
  
## Return Value

A **Recordset** object for which each row represents a child of the current **Record** object. For example, the children of a **Record** that represents a directory would be the files and subdirectories contained within the parent directory. 
  
## Remarks

The provider determines what columns exist in the returned **Recordset**. For example, a document source provider always returns a resource **Recordset**. 
  

