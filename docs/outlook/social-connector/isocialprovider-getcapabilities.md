---
title: "ISocialProviderGetCapabilities"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f40d5405-12e3-475b-b731-d2223ab70c1d
description: "Gets a string that describes provider capabilities."
---

# ISocialProvider::GetCapabilities

Gets a string that describes provider capabilities.
  
```cpp
HRESULT _stdcall GetCapabilities([out, retval] BSTR* result);
```

## Parameters

_result_
  
> [out] An XML string that represents the capabilities of an Outlook Social Connector (OSC) provider.
    
## Remarks

The returned  _result_ XML string must comply with the schema definition for the **capabilities** element, as defined in the XML schema for OSC provider extensibility. 
  
The provider must return a  _result_ string to enable subsequent calls from the OSC to the provider to operate correctly. 
  
## See also

- [ISocialProvider : IUnknown](isocialprovideriunknown.md)

