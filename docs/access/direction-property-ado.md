---
title: "Direction Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 51a94abb-7ce9-9adb-2b76-5391eb9f6863
---

# Direction Property (ADO)

Indicates whether the [Parameter](parameter-object-ado.md) represents an input parameter, an output parameter, an input and an output parameter, or if the parameter is the return value from a stored procedure. 
  
## Settings and Return Values

Sets or returns a [ParameterDirectionEnum](parameterdirectionenum.md) value. 
  
## Remarks

Use the **Direction** property to specify how a parameter is passed to or from a procedure. The **Direction** property is read/write; this allows you to work with providers that don't return this information or to set this information when you don't want ADO to make an extra call to the provider to retrieve parameter information. 
  
Not all providers can determine the direction of parameters in their stored procedures. In these cases, you must set the **Direction** property before you execute the query. 
  

