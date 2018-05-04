---
title: "ISocialProviderSocialNetworkGuid"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c07f71d-b906-4a7f-b20a-4a7f558dbf11
description: "Returns a GUID that represents a unique identifier for the social network."
---

# ISocialProvider::SocialNetworkGuid

Returns a GUID that represents a unique identifier for the social network.
  
```
[propget] HRESULT _stdcall SocialNetworkGuid([out, retval] GUID* guid);
```

## Property Value

A pointer to a GUID value that represents a unique identifier for the social network.
  
## Remarks

The GUID must be immutable and must not change even if the provider version changes.
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

