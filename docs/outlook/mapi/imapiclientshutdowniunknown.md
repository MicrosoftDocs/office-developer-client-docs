---
title: "IMAPIClientShutdown  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIClientShutdown
api_type:
- COM
ms.assetid: b6a5096f-ad27-48b3-b569-f33efc20fa72
description: "Last modified: March 09, 2015"
---

# IMAPIClientShutdown : IUnknown

  
  
**Applies to**: Outlook 
  
Enables a MAPI client to carry out fast shutdown of the client process. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |[IMAPISession](imapisessioniunknown.md) object  <br/> |
|Implemented by:  <br/> |MAPI subsystem  <br/> |
|Called by:  <br/> |MAPI client  <br/> |
|Interface identifier:  <br/> |IID_IMAPIClientShutdown  <br/> |
|Pointer type:  <br/> |LPMAPICLIENTSHUTDOWN  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) <br/> |Queries the MAPI subsystem for fast shutdown support that is provided by loaded MAPI providers.  <br/> |
|[NotifyProcessShutdown](imapiclientshutdown-notifyprocessshutdown.md) <br/> |Indicates the intention of the MAPI client to proceed with shut down.  <br/> |
|[DoFastShutdown](imapiclientshutdown-dofastshutdown.md) <br/> |Indicates the intention of the MAPI client to exit the client process immediately.  <br/> |
   
## Remarks

The purpose of fast shutdown is to allow a MAPI client and any loaded MAPI provider with which the MAPI client has an active MAPI session to save MAPI settings and data. This enables the MAPI client to disconnect all external references and exit without causing any data loss. A MAPI client that needs to perform fast shutdown must use the **IMAPIClientShutdown** interface. The MAPI client can obtain a pointer to this interface by calling the IUnknown::QueryInterface method on any [IMAPISession](imapisessioniunknown.md) object. 
  
A MAPI client always initiates a fast shutdown by calling the **IMAPIClientShutdown::QueryFastShutdown** method. The MAPI subsystem responds to the MAPI client's query by verifying whether loaded MAPI providers support the client's fast shutdown. The administrator can use Windows registry settings to help determine the level of provider support that is necessary for MAPI clients to proceed with fast shutdown. For more information, see [Fast Shutdown User Options](fast-shutdown-user-options.md).
  
To proceed with fast shutdown, the client calls the **IMAPIClientShutdown::NotifyProcessShutdown** method to indicate to the MAPI subsystem the intention to shut down. The client then calls the **IMAPIClientShutdown::DoFastShutdown** method to indicate that the client process is exiting immediately. 
  
For more information about fast shutdown, see [Fast Shutdown Overview](fast-shutdown-overview.md). For information about how to perform fast shutdown successfully, see [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md).
  
## See also



[MAPI Interfaces](mapi-interfaces.md)
  
[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

