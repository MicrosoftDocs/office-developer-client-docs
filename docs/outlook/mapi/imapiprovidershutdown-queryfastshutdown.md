---
title: "IMAPIProviderShutdownQueryFastShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProviderShutdown.QueryFastShutdown
api_type:
- COM
ms.assetid: 12069912-4b87-4945-9123-51106e0d2d54
description: "Last modified: July 23, 2011"
---

# IMAPIProviderShutdown::QueryFastShutdown

  
  
**Applies to**: Outlook 
  
Queries the MAPI provider for fast shutdown support. 
  
```
HRESULT QueryFastShutdown ();
```

## Return Value

S_OK
  
> The MAPI provider supports the MAPI client to do fast shutdown.
    
MAPI_E_NO_SUPPORT
  
> The MAPI provider does not support the MAPI client to do fast shutdown.
    
## Remarks

MAPI providers that do not need to support client fast shutdown should still implement the [IMAPIProviderShutdown](imapiprovidershutdowniunknown.md) interface, and have the **IMAPIProviderShutdown::QueryFastShutdown** method return MAPI_E_NO_SUPPORT. For Outlook as a MAPI client, this causes Outlook to wait for all external references to be released before it exits. 
  
Depending on the user's Windows registry setting for fast shutdown, not implementing the **IMAPIProviderShutdown** interface does not necessarily prevent a client fast shutdown. 
  
## See also

#### Reference

[IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md)
#### Concepts

[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

