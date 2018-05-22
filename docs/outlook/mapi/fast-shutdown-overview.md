---
title: "Fast Shutdown Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a7830d73-427c-4f8b-86f4-51e040c142c3
description: "Last modified: June 26, 2012"
---

# Fast Shutdown Overview

**Applies to**: Outlook 
  
Fast shutdown is a mechanism for a MAPI client to initiate a quick shutdown of the client process, notifying all providers with which the client has an active MAPI session to save data and settings before the client process exits. This topic describes the basic mechanism of fast shutdown. 

Starting in Microsoft Outlook 2010 and now including Microsoft Outlook 2013, the MAPI subsystem provides the [IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md) interface. Outlook and other MAPI clients can adopt fast shutdown as the default mechanism to exit the client process. A user-level setting in the Windows registry of the client computer controls the adoption of fast shutdown for all MAPI clients for that user on that computer. For details about the registry settings, see [Fast Shutdown User Options](fast-shutdown-user-options.md).
  
If a MAPI client needs to adopt fast shutdown, it must use the **IMAPIClientShutdown : IUnknown** interface. The following is the typical course of events when the client attempts to shut down: 
  
1. The MAPI client initiates the shutdown by calling the [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) method to determine whether the MAPI subsystem supports fast shutdown. 
    
2. The MAPI subsystem responds with the available fast shutdown support to the client's **IMAPIClientShutdown::QueryFastShutdown** call by using the following procedure: 
    
    1. The MAPI subsystem calls the [IMAPIProviderShutdown::QueryFastShutdown](imapiprovidershutdown-queryfastshutdown.md) method for each MAPI provider with which the MAPI client process has an active MAPI session, if the provider has implemented the [IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md) interface. 
        
       > [!NOTE]
       >  The MAPI subsystem always queries and notifies MAPI providers through the **IMAPIProviderShutdown : IUnknown** interface within each MAPI session in the following order:
       > 1. Transport providers
       > 2. Address book providers
       > 3. Store providers 
    
    2. Depending on the fast shutdown registry setting for that user on the client computer, the MAPI subsystem specifies the appropriate return code to **IMAPIClientShutdown::QueryFastShutdown**. The return code is either S_OK or MAPI_E_NO_SUPPORT.
        
    3. The MAPI client calls the [IMAPIClientShutdown::NotifyProcessShutdown](imapiclientshutdown-notifyprocessshutdown.md) method to indicate to the MAPI subsystem the intention to shut down. 
        
    4. The MAPI subsystem indicates to each loaded MAPI provider that the MAPI client will shut down. For those providers that have implemented the **IMAPIProviderShutdown : IUnknown** interface, the MAPI subsystem calls the corresponding [IMAPIProviderShutdown::NotifyProcessShutdown](imapiprovidershutdown-notifyprocessshutdown.md) method. 
        
    5. The MAPI client calls the [IMAPIClientShutdown::DoFastShutdown](imapiclientshutdown-dofastshutdown.md) method to indicate to the MAPI subsystem that the client process is exiting immediately. 
        
    6. The MAPI subsystem indicates to each loaded MAPI provider that the MAPI client process is exiting. For those providers that have implemented the **IMAPIProviderShutdown : IUnknown** interface, the MAPI subsystem calls the corresponding [IMAPIProviderShutdown::DoFastShutdown](imapiprovidershutdown-dofastshutdown.md) method. At this point, these MAPI providers should verify that all necessary actions, such as saving data and settings, are complete in preparation for the MAPI client to immediately disconnect all references and exit. 
    
## See also

- [Client Shutdown in MAPI](client-shutdown-in-mapi.md)
- [Fast Shutdown User Options](fast-shutdown-user-options.md)
- [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md)

