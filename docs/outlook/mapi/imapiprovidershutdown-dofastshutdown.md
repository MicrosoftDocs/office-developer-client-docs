---
title: "IMAPIProviderShutdownDoFastShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProviderShutdown.DoFastShutdown
api_type:
- COM
ms.assetid: d2b66a8e-2e28-4c32-af95-38d345c7bbd7
description: "Last modified: July 23, 2011"
---

# IMAPIProviderShutdown::DoFastShutdown

  
  
**Applies to**: Outlook 
  
Indicates to the MAPI provider that the MAPI client is exiting immediately, so that the MAPI provider will persist changes to prevent data loss.
  
```
HRESULT DoFastShutdown ();
```

## Return Value

S_OK
  
> The MAPI provider is ready for the MAPI client to exit immediately. 
    
## See also

#### Reference

[IMAPIProviderShutdown : IUnknown](imapiprovidershutdowniunknown.md)
#### Concepts

[Client Shutdown in MAPI](client-shutdown-in-mapi.md)

