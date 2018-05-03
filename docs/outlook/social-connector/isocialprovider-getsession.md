---
title: "ISocialProviderGetSession"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 371b48c5-6d77-4d2d-890c-bb234c7eaabc
description: "Gets an ISocialSession interface."
---

# ISocialProvider::GetSession

Gets an [ISocialSession](isocialsessioniunknown.md) interface. 
  
```
HRESULT _stdcall GetSession([out, retval] ISocialSession** session);
```

## Parameters

 _session_
  
> [out] An **ISocialSession** interface. 
    
## Remarks

The Outlook Social Connector (OSC) uses the **ISocialSession** interface to log on to the social network. 
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

