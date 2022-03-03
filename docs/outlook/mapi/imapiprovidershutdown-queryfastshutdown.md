---
title: "IMAPIProviderShutdownQueryFastShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProviderShutdown.QueryFastShutdown
api_type:
- COM
ms.assetid: 12069912-4b87-4945-9123-51106e0d2d54
---

# IMAPIProviderShutdown::QueryFastShutdown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Queries the MAPI provider for fast shutdown support. 
  
```cpp
HRESULT QueryFastShutdown ();
```

## Return value

S_OK
  
> The MAPI provider supports the MAPI client to do fast shutdown.
    
MAPI_E_NO_SUPPORT
  
> The MAPI provider does not support the MAPI client to do fast shutdown.
    
## Remarks

MAPI providers that do not need to support client fast shutdown should still implement the [IMAPIProviderShutdown](imapiprovidershutdowniunknown.md) interface, and have the **IMAPIProviderShutdown::QueryFastShutdown** method return MAPI_E_NO_SUPPORT. For Outlook as a MAPI client, this causes Outlook to wait for all external references to be released before it exits. 
  
Depending on the user's Windows registry setting for fast shutdown, not implementing the **IMAPIProviderShutdown** interface does not necessarily prevent a client fast shutdown. 
  
## See also



[IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

