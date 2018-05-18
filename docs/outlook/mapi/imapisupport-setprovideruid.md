---
title: "IMAPISupportSetProviderUID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.SetProviderUID
api_type:
- COM
ms.assetid: 58855843-9a2b-4e5d-9332-b1bfad8b45e4
description: "Last modified: July 23, 2011"
---

# IMAPISupport::SetProviderUID

  
  
**Applies to**: Outlook 
  
Registers a [MAPIUID](mapiuid.md) structure that uniquely represents the service provider. 
  
```cpp
HRESULT SetProviderUID(
LPMAPIUID lpProviderID,
ULONG ulFlags
);
```

## Parameters

 _lpProviderID_
  
> [in] A pointer to the **MAPIUID** structure that identifies the address book or message store provider. 
    
 _ulFlags_
  
> Reserved; must be zero.
    
## Return value

S_OK 
  
> The **MAPIUID** structure was successfully registered. 
    
## Remarks

The **IMAPISupport::SetProviderUID** method is implemented for address book and message store provider support objects. These providers call **SetProviderUID** to register a unique identifier described in the **MAPIUID** structure that is pointed to by  _lpProviderID_. Providers include this identifier in all of the entry identifiers that they create. 
  
MAPI uses the **MAPIUID** structure when it sends outbound messages to the MAPI spooler and to determine the appropriate provider for handling client requests. For example, when a client calls the [IMAPISession::OpenEntry](imapisession-openentry.md) method, MAPI examines the **MAPIUID** portion of the entry identifier, maps it to the provider that passed it to **SetProviderUID**, and calls that provider's **OpenEntry**. 
  
## Notes to Callers

Call **SetProviderUID** at logon time to register your **MAPIUID** structure. MAPI allows address book and message store providers to register multiple identifiers. When you make multiple calls to **SetProviderUID**, it always adds the **MAPIUID** structure to the provider's set of **MAPIUID** structures, even if the **MAPIUID** is a duplicate. **SetProviderUID** cannot remove a **MAPIUID**. 
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

