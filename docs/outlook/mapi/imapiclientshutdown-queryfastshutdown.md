---
title: "IMAPIClientShutdownQueryFastShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIClientShutdown.QueryFastShutdown
api_type:
- COM
ms.assetid: b743b5b6-4a7c-46b8-99eb-afd13ee947db
description: "Last modified: July 23, 2011"
---

# IMAPIClientShutdown::QueryFastShutdown

  
  
**Applies to**: Outlook 
  
Queries the MAPI subsystem for fast shutdown support that is provided by loaded MAPI providers.
  
```cpp
HRESULT QueryFastShutdown ();
```

## Return value

S_OK
  
> The MAPI subsystem supports the MAPI client to do fast shutdown.
    
MAPI_E_NO_SUPPORT
  
> The MAPI provider does not support the MAPI client to do fast shutdown.
    
## Remarks

Whether the MAPI subsystem supports the MAPI client to do fast shutdown depends on the user's Windows registry setting or the default behavior of the MAPI client for fast shutdown. It also depends on the ability of the loaded MAPI providers to support fast shutdown. For more information, see [Fast Shutdown User Options](fast-shutdown-user-options.md).
  
## See also



[IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

