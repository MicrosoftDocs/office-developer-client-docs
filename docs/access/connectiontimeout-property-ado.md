---
title: "ConnectionTimeout Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: efc39fd8-afce-5ac0-2fff-cbb55c1a444d
---

# ConnectionTimeout Property (ADO)

Indicates how long to wait while establishing a connection before terminating the attempt and generating an error.
  
## Settings and Return Values

Sets or returns a **Long** value that indicates, in seconds, how long to wait for the connection to open. Default is 15. 
  
## Remarks

Use the **ConnectionTimeout** property on a [Connection](connection-object-ado.md) object if delays from network traffic or heavy server use make it necessary to abandon a connection attempt. If the time from the **ConnectionTimeout** property setting elapses prior to the opening of the connection, an error occurs and ADO cancels the attempt. If you set the property to zero, ADO will wait indefinitely until the connection is opened. Make sure the provider to which you are writing code supports the **ConnectionTimeout** functionality. 
  
The **ConnectionTimeout** property is read/write when the connection is closed and read-only when it is open. 
  

