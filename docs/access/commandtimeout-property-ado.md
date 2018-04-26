---
title: "CommandTimeout Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- ado210.chm1231124
  
localization_priority: Normal
ms.assetid: a0b6209c-9feb-08ae-002a-15d1d20734a8
---

# CommandTimeout Property (ADO)

Indicates how long to wait while executing a command before terminating the attempt and generating an error.
  
## Settings and Return Values

Sets or returns a **Long** value that indicates, in seconds, how long to wait for a command to execute. Default is 30. 
  
## Remarks

Use the **CommandTimeout** property on a [Connection](connection-object-ado.md) object or [Command](command-object-ado.md) object to allow the cancellation of an [Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) method call, due to delays from network traffic or heavy server use. If the interval set in the **CommandTimeout** property elapses before the command completes execution, an error occurs and ADO cancels the command. If you set the property to zero, ADO will wait indefinitely until the execution is complete. Make sure the provider and data source to which you are writing code support the **CommandTimeout** functionality. 
  
The **CommandTimeout** setting on a **Connection** object has no effect on the **CommandTimeout** setting on a **Command** object on the same **Connection**; that is, the **Command** object's **CommandTimeout** property does not inherit the value of the **Connection** object's **CommandTimeout** value. 
  
On a **Connection** object, the **CommandTimeout** property remains read/write after the **Connection** is opened. 
  

