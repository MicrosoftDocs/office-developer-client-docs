---
title: "ConnectComplete and Disconnect Events (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8ecb080b-7fc9-7565-25bd-bd57b983750d
---

# ConnectComplete and Disconnect Events (ADO)

The **ConnectComplete** event is called after a connection  *starts*  . The **Disconnect** event is called after a connection  *ends*  . 
  
## Syntax

 **ConnectComplete** *pError*  ,  *adStatus*  ,  *pConnection* 
  
 **Disconnect** *adStatus*  ,  *pConnection* 
  
## Parameters

-  *pError* 
    
- An [Error](error-object-ado.md) object. It describes the error that occurred if the value of  *adStatus*  is **adStatusErrorsOccurred**; otherwise it is not set. 
    
-  *adStatus* 
    
- [EventStatusEnum](eventstatusenum.md)
    
    When **ConnectComplete** is called, this parameter is set to **adStatusCancel** if a **WillConnect** event has requested cancellation of the pending connection. 
    
    Before either event returns, set this parameter to **adStatusUnwantedEvent** to prevent subsequent notifications. However, closing and reopening the [Connection](connection-object-ado.md) causes these events to occur again. 
    
-  *pConnection* 
    
- The **Connection** object for which this event applies. 
    

