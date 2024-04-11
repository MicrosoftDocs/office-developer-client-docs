---
title: "Best Practices for Fast Shutdown"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ae8a9214-e53f-4c57-8dbe-aa7cc6903aa8
 
 
---

# Best Practices for Fast Shutdown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This topic recommends best practices for administrators, MAPI clients, and MAPI providers to use Windows registry settings and the fast shutdown interfaces to minimize data loss during client shutdown.
  
- For a MAPI client to carry out fast shutdown successfully so that provider processes do not incur data loss, the MAPI client should first call the [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) method. The client should then proceed with the [IMAPIClientShutdown::NotifyProcessShutdown](imapiclientshutdown-notifyprocessshutdown.md) and [IMAPIClientShutdown::DoFastShutdown](imapiclientshutdown-dofastshutdown.md) methods based on the MAPI subsystem's support for fast shutdown, as indicated by the return value of **IMAPIClientShutdown::QueryFastShutdown**. As a MAPI client, Microsoft Outlook does not call **IMAPIClientShutdown::NotifyProcessShutdown** or **IMAPIClientShutdown::DoFastShutdown** if **IMAPIClientShutdown::QueryFastShutdown** returns an error. If the administrator has disabled fast shutdown in the Windows registry, the MAPI subsystem would return MAPI_E_NO_SUPPORT to **IMAPIClientShutdown::QueryFastShutdown**. In this case, the MAPI subsystem would not inform MAPI providers of an immediate client process exit. Therefore, if a MAPI client disregards this error return code, proceeds to do fast shutdown, and disconnects all external references, all loaded MAPI providers will have data loss. 
    
- MAPI providers should implement the [IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md) interface to carry out timely and necessary steps to avoid data loss due to the client disconnecting external references before the client exits. A provider should postpone everything else that is nonessential to saving data to its primary data store. For example, a transport provider should postpone unnecessary background operations that check for new mail, an address book provider should postpone downloading recent changes from its server, and a store provider should postpone maintenance tasks such as compacting or indexing. 
    
- Users who want MAPI clients to exit as soon as they close them should use the default registry setting that enables fast shutdown unless a provider opts out.
    
- Once a MAPI client calls **IMAPIClientShutdown::DoFastShutdown**, it should not make any additional calls to MAPI, including the [MAPIUninitialize](mapiuninitialize.md) function. The client should not use MAPI for the rest of the client process's lifetime. 
    
- A MAPI client should never directly call a provider's **IMAPIProviderShutdown** interface. MAPI clients should always use the [IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md) interface. 
    
- If a MAPI provider needs to ensure that fast shutdown is not used while it is loaded, it should implement the **IMAPIProviderShutdown** interface and return MAPI_E_NO_SUPPORT for the **IMAPIProviderShutdown::QueryFastShutdown** method. However, for MAPI clients such as Outlook, this will cause the client to abandon fast shutdown and take a longer time to shut down. 
    
## See also



[Client Shutdown in MAPI](client-shutdown-in-mapi.md)
  
[Fast Shutdown Overview](fast-shutdown-overview.md)
  
[Fast Shutdown User Options](fast-shutdown-user-options.md)

