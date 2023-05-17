---
title: "IMAPIProviderShutdown  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProviderShutdown
api_type:
- COM
ms.assetid: fd86c8a5-f251-46c3-ace9-515e94e504ac
description: "Allows the MAPI subsystem to inform a MAPI provider of the fast shutdown of a MAPI client, so that the MAPI provider can respond to the shutdown."
---

# IMAPIProviderShutdown : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Allows the MAPI subsystem to inform a MAPI provider of the fast shutdown of a MAPI client, so that the MAPI provider can respond to the shutdown.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Provider objects: [IXPProvider](ixpprovideriunknown.md), [IABProvider](iabprovideriunknown.md), or [IMSProvider](imsprovideriunknown.md) <br/> |
|Implemented by:  <br/> |MAPI provider  <br/> |
|Called by:  <br/> |MAPI subsystem  <br/> |
|Interface identifier:  <br/> |IID_IMAPIProviderShutdown  <br/> |
|Pointer type:  <br/> |LPMAPIPROVIDERSHUTDOWN  <br/> |
   
## Vtable order

|Property |Value |
|:-----|:-----|
|[QueryFastShutdown](imapiprovidershutdown-queryfastshutdown.md) <br/> |Queries the MAPI provider for fast shutdown support. |
|[NotifyProcessShutdown](imapiprovidershutdown-notifyprocessshutdown.md) <br/> |Indicates to the MAPI provider that a MAPI client is going to do a fast shutdown, so that the provider can take actions to prevent data loss. |
|[DoFastShutdown](imapiprovidershutdown-dofastshutdown.md) <br/> |Indicates to the MAPI provider that the MAPI client is exiting immediately, so that the MAPI provider will persist changes to prevent data loss. |
   
## Remarks

Fast shutdown allows a MAPI client to exit its process within a short time, hopefully after the client and loaded MAPI providers have saved MAPI settings and data. The MAPI client always initiates a fast shutdown and should query the MAPI subsystem for fast shutdown support from the loaded MAPI providers. An administrator can set the Windows registry at the user level to specify the level of provider support that is necessary to allow fast shutdown of all MAPI clients. For more information about the registry settings, see [Fast Shutdown User Options](fast-shutdown-user-options.md). However, for fast shutdown to successfully occur without data loss, MAPI providers should implement the **IMAPIProviderShutdown** interface. 
  
A MAPI provider that needs to support client fast shutdown should return S_OK to the MAPI subsystem in the **IMAPIProviderShutdown::QueryFastShutdown** method. When the MAPI subsystem subsequently calls the **IMAPIProviderShutdown::NotifyProcessShutdown** and **IMAPIProviderShutdown::DoFastShutdown** methods, the MAPI provider should take necessary actions to save MAPI settings and data and prepare for the client's exit. 
  
MAPI providers that do not need to support client fast shutdown should still implement the **IMAPIProviderShutdown** interface, and have the **IMAPIProviderShutdown::QueryFastShutdown** method return MAPI_E_NO_SUPPORT. For Outlook as a MAPI client, this causes Outlook to wait for all external references to be released before it exits. 
  
Depending on the user's Windows registry setting for fast shutdown, not implementing the **IMAPIProviderShutdown** interface does not necessarily prevent a client fast shutdown. 
  
For more information about the process of fast shutdown, see [Fast Shutdown Overview](fast-shutdown-overview.md). For information about how to carry out fast shutdown successfully, see [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md).
  
## See also



[MAPI Interfaces](mapi-interfaces.md)
  
[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

