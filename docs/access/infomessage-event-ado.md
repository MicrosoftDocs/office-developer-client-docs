---
title: "InfoMessage Event (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5d4f487f-96c8-4cf6-60ab-583510d3096f

---

# InfoMessage Event (ADO)

The **InfoMessage** event is called whenever a warning occurs during a **ConnectionEvent** operation. 
  
## Syntax

 **InfoMessage** *pError*  ,  *adStatus*  ,  *pConnection* 
  
## Parameters

-  *pError* 
    
- An [Error](error-object-ado.md) object. This parameter contains any errors that are returned. If multiple errors are returned, enumerate the **Errors** collection to find them. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    Before this event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. 
    
-  *pConnection* 
    
- A [Connection](connection-object-ado.md) object. The connection for which the warning occurred. For example, warnings can occur when opening a **Connection** object or executing a [Command](command-object-ado.md) on a **Connection**. 
    

