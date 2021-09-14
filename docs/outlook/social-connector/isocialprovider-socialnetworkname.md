---
title: "ISocialProviderSocialNetworkName"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 96f32db2-d654-4e72-88d1-ef955e3ff42b
description: "Returns a string that represents the social network name."
---

# ISocialProvider::SocialNetworkName

Returns a string that represents the social network name. 
  
```cpp
[propget] HRESULT _stdcall SocialNetworkName([out, retval] BSTR* networkName);
```

## Property value

A string that contains the social network name.
  
## Remarks

Outlook Social Connector (OSC) providers should localize the social network name.
  
## See also

- [ISocialProvider : IUnknown](isocialprovideriunknown.md)

