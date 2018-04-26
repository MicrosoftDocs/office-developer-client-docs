---
title: "MarshalOptions Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: dc9c4e94-0725-210d-8251-079054541142

---

# MarshalOptions Property (ADO)

Indicates which records are to be marshaled back to the server.
  
## Settings And Return Values

Sets or returns a [MarshalOptionsEnum](marshaloptionsenum.md) value. The default value is **adMarshalAll**. 
  
## Remarks

When using a client-side [Recordset](recordset-object-ado.md), records that have been modified on the client are written back to the middle tier or Web server through a technique called marshaling, the process of packaging and sending interface method parameters across thread or process boundaries. Setting the **MarshalOptions** property can improve performance when modified remote data is marshaled for updating back to the middle tier or Web server. 
  
 **Remote Data Service Usage** This property is used only on a client-side **Recordset**. 
  

