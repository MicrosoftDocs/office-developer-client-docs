---
title: "ISocialProviderSocialNetworkIcon"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8b51675f-77b7-4df0-8496-b1e8958c6544
description: "Returns an array of bytes that represents the icon for the social network."
 
 
---

# ISocialProvider::SocialNetworkIcon

Returns an array of bytes that represents the icon for the social network. 
  
```
[propget] HRESULT _stdcall SocialNetworkIcon([out, retval] SAFEARRAY(unsigned char)* networkIcon);
```

## Property Value

A pointer to a structure that specifies an array of bytes that contains the icon for the social network.
  
## Remarks

The supported picture resources are .bmp, .jpeg, and .png formats.
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

