---
title: "IMSProviderShutdown"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSProvider.Shutdown
api_type:
- COM
ms.assetid: 9ca1861d-9bc9-485a-9807-a598b869e5a2
description: "Last modified: July 23, 2011"
---

# IMSProvider::Shutdown

  
  
**Applies to**: Outlook 
  
Closes a message store provider in an orderly fashion.
  
```cpp
HRESULT Shutdown(
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [in] Reserved; must be a pointer to zero.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

MAPI calls the **IMSProvider::Shutdown** method just before releasing the message store provider object. MAPI releases all logon objects for a provider before calling **Shutdown** for that provider. 
  
## See also



[IMSProvider : IUnknown](imsprovideriunknown.md)

