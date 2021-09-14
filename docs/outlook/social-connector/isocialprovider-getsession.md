---
title: "ISocialProviderGetSession"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 371b48c5-6d77-4d2d-890c-bb234c7eaabc
description: "Gets an ISocialSession interface."
---

# ISocialProvider::GetSession

Gets an [ISocialSession](isocialsessioniunknown.md) interface. 
  
```cpp
HRESULT _stdcall GetSession([out, retval] ISocialSession** session);
```

## Parameters

_session_
  
> [out] An **ISocialSession** interface. 
    
## Remarks

The Outlook Social Connector (OSC) uses the **ISocialSession** interface to log on to the social network. 
  
## See also

- [ISocialProvider : IUnknown](isocialprovideriunknown.md)

