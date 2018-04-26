---
title: "ActiveCommand Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 41c19008-cbf7-ade9-b4ab-e908a16784ac
---

# ActiveCommand Property (ADO)

Indicates the [Command](command-object-ado.md) object that created the associated [Recordset](recordset-object-ado.md) object. 
  
## Return Value

Returns a **Variant** that contains a **Command** object. Default is a null object reference. 
  
## Remarks

The **ActiveCommand** property is read-only. 
  
If a **Command** object was not used to create the current **Recordset**, then a **Null** object reference is returned. 
  
Use this property to find the associated **Command** object when you are given only the resulting **Recordset** object. 
  

