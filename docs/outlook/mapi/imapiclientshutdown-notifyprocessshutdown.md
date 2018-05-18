---
title: "IMAPIClientShutdownNotifyProcessShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIClientShutdown.NotifyProcessShutdown
api_type:
- COM
ms.assetid: 42dd7889-5e00-419a-91e7-8350be4efd35
description: "Last modified: July 23, 2011"
---

# IMAPIClientShutdown::NotifyProcessShutdown

  
  
**Applies to**: Outlook 
  
Indicates the intention of the MAPI client to proceed with shut down.
  
```cpp
HRESULT NotifyProcessShutdown ();
```

## Return value

S_OK
  
> The MAPI subsystem has attempted to notify loaded MAPI providers that the MAPI client is going to do a fast shutdown.
    
## Remarks

To avoid data loss from the fast shutdown of a MAPI client, MAPI clients should call the **IMAPIClientShutdown::NotifyProcessShutdown** and [IMAPIClientShutdown::DoFastShutdown](imapiclientshutdown-dofastshutdown.md) methods based on the S_OK result returned by the MAPI subsystem in the [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) method. For more information, see [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md).
  
## See also



[IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md)


[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

