---
title: "IPSTOVERRIDE1GetPersistedRegistrations"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IPSTOVERRIDE1.GetPersistedRegistrations
api_type:
- COM
ms.assetid: 027092f0-f2d6-49e8-a8d0-8926824953a2
---

# IPSTOVERRIDE1::GetPersistedRegistrations

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the list of registrations for the Personal Folders (.pst) file.
  
```cpp
HRESULT GetPersistedRegistration(SPropValue **ppmval);
```

## Parameters

 _ppmval_
  
> [in] A pointer to a pointer to an [SPropValue](spropvalue.md) structure. The ulPropTag member of this structure is of the type PT_MV_UNICODE, and the MVszW value member will be an array of null-terminated Unicode strings. These strings are paths to DLLs for which registration has been persisted. 
    
> [!NOTE]
> .pst support for ANSI is not implemented. 
  
## Return value

S_OK 
  
> The function call was successful.
    
## See also



[IPSTOVERRIDE1 : IUnknown](ipstoverride1iunknown.md)
  
[IPSTOVERRIDEREQ : IUnknown](ipstoverridereqiunknown.md)

