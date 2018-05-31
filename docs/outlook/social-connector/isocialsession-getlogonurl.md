---
title: "ISocialSessionGetLogonUrl"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d61bab07-acb3-433b-8783-c3fe110a5582
description: "Gets a string that represents a URL that is used for presenting a browser-based form to the user during web authentication."
---

# ISocialSession::GetLogonUrl

Gets a string that represents a URL that is used for presenting a browser-based form to the user during web authentication.
  
```cpp
HRESULT _stdcall GetLogonUrl([out, retval] BSTR* url);
```

## Parameters

_url_
  
> [out] A string that contains a URL for the form used in web authentication.
    
## Remarks

After the form is presented to the user, the [ISocialSession::LogonWeb](isocialsession-logonweb.md) method is called with an empty string for the  _connectIn_ parameter. 
  
## See also

- [ISocialSession : IUnknown](isocialsessioniunknown.md)

