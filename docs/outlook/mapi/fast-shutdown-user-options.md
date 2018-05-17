---
title: "Fast shutdown user options"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 220aeab5-20f6-4520-96c9-8aaa0e8ea15b
description: "Last modified: June 26, 2012"
---

# Fast shutdown user options

**Applies to**: Outlook 
  
This topic describes the three Windows registry settings that are available, starting in Microsoft Outlook 2010 and now including Microsoft Outlook 2013, for fast shutdown of a user's MAPI clients. Administrators can use these registry settings to specify the preferred client shutdown behavior depending on the MAPI providers' support for client fast shutdown. The administrator's setting, in turn, determines how the MAPI subsystem responds to the MAPI client's call to [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) in terms of available fast shutdown support. 
  
Even though a registry setting reflects the administrator's preference at the user level for fast shutdown for all MAPI clients, a MAPI client developer can decide whether the client supports fast shutdown independently of other MAPI clients and the administrator's registry setting. Nonetheless, for fast shutdown to take place successfully, the user must have the necessary registry setting, a MAPI client must initiate the fast shutdown by using the [IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md) interface, and MAPI providers that work with the client should implement the [IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md) interface to support client fast shutdown. 
  
The following list describes the three user-level options.
  
### Option 1: The MAPI subsystem enables fast shutdown, unless MAPI providers explicitly opt out 
    
Starting in Outlook 2010, this is the default behavior when Outlook is the MAPI client; it is not necessarily the default behavior for other MAPI clients. To explicitly specify this option for Outlook, administrators can choose to set the following registry key and value.
    
Registry key:
  
>  `[HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\14.0\Outlook\Options\Shutdown]`
    
Value:
  
>  `"FastShutdownBehavior"=dword:00000000`
    
When a MAPI client initiates a fast shutdown and calls **IMAPIClientShutdown::QueryFastShutdown** to query for fast shutdown support, the MAPI subsystem responds to the query by returning S\_OK as long as no MAPI provider that has an active MAPI session with the MAPI client has explicitly opted out of fast shutdown support. 

A MAPI provider opts out of fast shutdown by implementing the [IMAPIProviderShutdown::QueryFastShutdown](imapiprovidershutdown-queryfastshutdown.md) method to return an error (MAPI\_E\_NO\_SUPPORT). If one or more MAPI providers return an error in **IMAPIProviderShutdown::QueryFastShutdown**, the MAPI subsystem returns MAPI_\E_\NO\_SUPPORT to **IMAPIClientShutdown::QueryFastShutdown**. 

Unless a MAPI provider opts out, the MAPI subsystem returns S\_OK, even if one or more providers have not implemented the **IMAPIProviderShutdown : IUnknown** interface. 
    
### Option 2: The MAPI subsystem enables fast shutdown only if every MAPI provider explicitly opts in 
    
Administrators must explicitly set the following registry key and value to specify this preference for client fast shutdown.
    
Registry key:
  
>  `[HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\14.0\Outlook\Options\Shutdown]`
    
Value:
  
>  `"FastShutdownBehavior"=dword:00000001`
    
When a MAPI client initiates a fast shutdown and calls **IMAPIClientShutdown::QueryFastShutdown** to query for fast shutdown support, the MAPI subsystem responds to the query by returning S\_OK if all MAPI providers that have active sessions with the MAPI client support fast shutdown. A MAPI provider demonstrates its support by implementing **IMAPIProviderShutdown::QueryFastShutdown** to return a non-error code (S\_OK). 

If one or more such MAPI providers return MAPI\_E\_NO\_SUPPORT, or do not implement **IMAPIProviderShutdown::QueryFastShutdown**, the MAPI subsystem returns an error code to **IMAPIClientShutdown::QueryFastShutdown**.
    
### Option 3: An administrator disables support for client fast shutdown
    
Administrators must explicitly set the following registry key and value to disable support for client fast shutdown.
    
Registry key:
  
>  `[HKEY_CURRENT_USER\Software\Policies\Microsoft\Office\14.0\Outlook\Options\Shutdown]`
    
Value:
  
>  `"FastShutdownBehavior"=dword:00000002`
    
When a MAPI client initiates a fast shutdown and calls **IMAPIClientShutdown::QueryFastShutdown** to query for fast shutdown support, the MAPI subsystem responds to the query by returning MAPI_E_NO_SUPPORT, regardless of whether any MAPI provider supports fast shutdown. Under this registry setting, the MAPI subsystem never calls the **IMAPIProviderShutdown::QueryFastShutdown** or [IMAPIProviderShutdown::DoFastShutdown](imapiprovidershutdown-dofastshutdown.md) method of any of the providers. 
    
## See also

- [Client Shutdown in MAPI](client-shutdown-in-mapi.md)
- [Fast Shutdown Overview](fast-shutdown-overview.md)
- [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md)

