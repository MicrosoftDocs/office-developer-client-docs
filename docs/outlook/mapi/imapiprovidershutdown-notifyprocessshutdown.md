---
title: "IMAPIProviderShutdownNotifyProcessShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProviderShutdown.NotifyProcessShutdown
api_type:
- COM
ms.assetid: a00d71b1-d705-40d5-b667-f91b57db85da
---

# IMAPIProviderShutdown::NotifyProcessShutdown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates to the MAPI provider that a MAPI client is going to do a fast shutdown, so that the provider can take actions to prevent data loss.
  
```cpp
HRESULT NotifyProcessShutdown ();
```

## Return value

S_OK
  
> The MAPI provider is taking actions to prevent data loss when the MAPI client shuts down.
    
## See also



[IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

