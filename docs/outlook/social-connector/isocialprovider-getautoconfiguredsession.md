---
title: "ISocialProviderGetAutoConfiguredSession"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d8d41ced-c2bb-482e-b0bc-1b46c82121bd
description: "Gets an automatically configured ISocialSession interface."
 
 
---

# ISocialProvider::GetAutoConfiguredSession

Gets an automatically configured [ISocialSession](isocialsessioniunknown.md) interface. 
  
```
HRESULT _stdcall GetAutoConfiguredSession([out, retval] ISocialSession** session);
```

## Parameters

 _session_
  
> [out] An **ISocialSession** interface. 
    
## Remarks

The returned **ISocialSession** interface is automatically logged on to the network, based on a method that is specific to the provider. 
  
The provider should return the OSC_E_NOT_IMPLEMENTED error if the social network does not support automatic configuration. For information about error codes, see [Outlook Social Connector Provider Error Codes](outlook-social-connector-provider-error-codes.md).
  
## See also

#### Reference

[ISocialProvider : IUnknown](isocialprovideriunknown.md)

