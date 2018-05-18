---
title: "ISocialSessionGetNetworkIdentifier"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 534e404f-54c6-4d2b-a8d0-d2ee990a972f
description: "Gets a string that represents a unique social network identifier for a given social network connection."
---

# ISocialSession::GetNetworkIdentifier

Gets a string that represents a unique social network identifier for a given social network connection. 
  
```
HRESULT _stdcall GetNetworkIdentifier([out, retval] BSTR* networkIdentifier);
```

## Parameters

 _networkIdentifier_
  
> [out] A string that contains a unique social network identifier.
    
## Remarks

A unique network identifier is a string that identifies the Outlook Social Connector (OSC) provider social network. This method can also return E_NOTIMPL.
  
## See also



[ISocialSession : IUnknown](isocialsessioniunknown.md)

