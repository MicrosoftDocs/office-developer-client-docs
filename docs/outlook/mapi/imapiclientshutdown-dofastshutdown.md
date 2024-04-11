---
title: "IMAPIClientShutdownDoFastShutdown"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIClientShutdown.DoFastShutdown
api_type:
- COM
ms.assetid: 310cba9a-a343-484d-a029-fcd51b731460
---

# IMAPIClientShutdown::DoFastShutdown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the intention of the MAPI client to exit the client process immediately.
  
```cpp
HRESULT DoFastShutdown ();
```

## Return value

S_OK
  
> The MAPI subsystem has indicated to loaded MAPI providers that the MAPI client is exiting immediately, and the MAPI providers are ready for the client exit.
    
MAPI_E_NO_SUPPORT
  
> The MAPI subsystem does not support client fast shutdown.
    
## Remarks

To avoid data loss from the fast shutdown of a MAPI client, MAPI clients should call the [IMAPIClientShutdown::NotifyProcessShutdown](imapiclientshutdown-notifyprocessshutdown.md) and **IMAPIClientShutdown::DoFastShutdown** methods based on the S_OK result returned by the MAPI subsystem in the [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) method. For more information, see [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md).
  
## See also



[IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

