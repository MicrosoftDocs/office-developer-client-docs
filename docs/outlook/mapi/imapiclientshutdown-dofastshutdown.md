---
title: "IMAPIClientShutdownDoFastShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIClientShutdown.DoFastShutdown
api_type:
- COM
ms.assetid: 310cba9a-a343-484d-a029-fcd51b731460
description: "Last modified: July 23, 2011"
---

# IMAPIClientShutdown::DoFastShutdown

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Indicates the intention of the MAPI client to exit the client process immediately.
  
```
HRESULT DoFastShutdown ();
```

## Return Value

S_OK
  
> The MAPI subsystem has indicated to loaded MAPI providers that the MAPI client is exiting immediately, and the MAPI providers are ready for the client exit.
    
MAPI_E_NO_SUPPORT
  
> The MAPI subsystem does not support client fast shutdown.
    
## Remarks

To avoid data loss from the fast shutdown of a MAPI client, MAPI clients should call the [IMAPIClientShutdown::NotifyProcessShutdown](imapiclientshutdown-notifyprocessshutdown.md) and **IMAPIClientShutdown::DoFastShutdown** methods based on the S_OK result returned by the MAPI subsystem in the [IMAPIClientShutdown::QueryFastShutdown](imapiclientshutdown-queryfastshutdown.md) method. For more information, see [Best Practices for Fast Shutdown](best-practices-for-fast-shutdown.md).
  
## See also

#### Reference

[IMAPIClientShutdown : IUnknown](imapiclientshutdowniunknown.md)
#### Concepts

[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

