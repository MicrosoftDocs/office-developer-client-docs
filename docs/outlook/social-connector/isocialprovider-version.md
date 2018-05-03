---
title: "ISocialProviderVersion"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dfc92878-ab8b-4721-aee8-997c56a8e45b
description: "Returns a string that represents the version number of the provider for this social network."
---

# ISocialProvider::Version

Returns a string that represents the version number of the provider for this social network. 
  
```
[propget] HRESULT _stdcall Version([out, retval] BSTR* Version);
```

## Property Value

A string that contains the version number of the provider.
  
## Remarks

The version string should use the  _MajorVersion_. _MinorVersion_ format (for example, 1.4730). 
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

