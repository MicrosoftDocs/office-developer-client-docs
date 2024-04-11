---
title: "IMAPIProviderShutdownDoFastShutdown"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProviderShutdown.DoFastShutdown
api_type:
- COM
ms.assetid: d2b66a8e-2e28-4c32-af95-38d345c7bbd7
---

# IMAPIProviderShutdown::DoFastShutdown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates to the MAPI provider that the MAPI client is exiting immediately, so that the MAPI provider will persist changes to prevent data loss.
  
```cpp
HRESULT DoFastShutdown ();
```

## Return value

S_OK
  
> The MAPI provider is ready for the MAPI client to exit immediately. 
    
## See also



[IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

