---
title: "ISocialProviderLoad"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6356f7bf-e3a1-4294-ad6e-df77bdd0356c
description: "Initializes the Outlook Social Connector (OSC) provider."
---

# ISocialProvider::Load

Initializes the Outlook Social Connector (OSC) provider.
  
```
HRESULT _stdcall Load([in] BSTR socialProviderInterfaceVersion, [in] BSTR languageTag);
```

## Parameters

 _socialProviderInterfaceVersion_
  
> [in] The version of the OSC provider interfaces expected by the OSC.
    
 _languageTag_
  
> [in] The Internet Engineering Task Force (IETF) language tag, defined by [[RFC4646]](http://www.ietf.org/rfc/rfc4646.txt) and [[RFC4647]](http://www.ietf.org/rfc/rfc4647.txt), that represents the current Outlook user-interface language.
    
## Remarks

The version format for the  _socialProviderInterfaceVersion_ parameter is  _X_. _xxxx_, where  _X_ is the major version and  _xxxx_ is the minor version of the OSC. For Office 2013, check for the major version being 15. 
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

