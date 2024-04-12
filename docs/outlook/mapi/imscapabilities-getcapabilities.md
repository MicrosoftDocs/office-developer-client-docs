---
title: "IMSCapabilitiesGetCapabilities"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMSCapabilities.GetCapabilities
api_type:
- COM
ms.assetid: c77a8ef1-0730-d458-b35f-451d3f450fac
---

# IMSCapabilities::GetCapabilities

  
**Applies to**: Outlook 2013 | Outlook 2016
  
Gets information about what a store can support based on the specified selector.
  
```cpp
ULONG GetCapabilities( 
MSCAP_SELECTOR mscapSelector 
);
```

## Parameters

 *mscapSelector* 
  
> [in] Selector indicating which capabilities to return.

## Return value

MSCAP_SECURE_FOLDER_HOMEPAGES
  
> Support for folder homepages in a non-default store. This can be returned if **MSCAP_SEL_FOLDER** is specified in *mscapSelector*.

MSCAP_RES_ANNOTATION
  
> If a restriction contains any invalid arguments such as invalid properties, the store ignores the invalid arguments and processes only the valid arguments. This can be returned if **MSCAP_SEL_RESTRICTION** is specified in *mscapSelector*.

NULL
  
> The store does not support any capability based on the given selector.
