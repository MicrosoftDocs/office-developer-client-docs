---
title: "ISocialProviderDefaultSiteUrls"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 322ea2e9-d6c9-48f9-a927-7162346d16a4
description: "Returns an array of strings that specify site URLs for the Outlook Social Connector (OSC) provider."
---

# ISocialProvider::DefaultSiteUrls

Returns an array of strings that specify site URLs for the Outlook Social Connector (OSC) provider.
  
```cpp
[propget] HRESULT _stdcall DefaultSiteUrls([out, retval] SAFEARRAY(BSTR)* siteUrls);
```

## Property value

A pointer to a structure that specifies an array of strings that represent site URLs for the OSC provider.
  
## Remarks

A provider can support multiple site URLs. The OSC sets the [ISocialSession::SiteUrl](isocialsession-siteurl.md) property to inform the provider of the selected site URL. 
  
The OSC uses the first element of the array as the default site URL. A provider can return additional elements in the site URL array, but the OSC does not use them. 
  
## See also

- [ISocialProvider : IUnknown](isocialprovideriunknown.md)

