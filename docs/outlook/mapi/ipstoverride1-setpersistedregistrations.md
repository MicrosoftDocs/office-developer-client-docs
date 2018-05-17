---
title: "IPSTOVERRIDE1SetPersistedRegistrations"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPSTOVERRIDE1.SetPersistedRegistrations
api_type:
- COM
ms.assetid: 5f4b62db-a759-41a2-9bea-29fc04b2962b
description: "Last modified: November 08, 2011"
---

# IPSTOVERRIDE1::SetPersistedRegistrations

**Applies to**: Outlook 
  
Registers Personal Folders (.pst) files for automatic unlocking, avoiding further calls to the HrTrustedPSTOverrideHandlerCallback.
  
```
HRESULT SetPersistedRegistrations(
  SPropValue *pmval
);
```

## Parameters

_pmval_
  
> [in] An [SPropValue](spropvalue.md) structure that contains a pointer to the path of the dynamic-link library (DLL) to register. The structure has the following characteristics: 
    
   - A ulPropTag of [PROP_TAG](prop_tag.md)(PT_MV_UNICODE, PROP_ID_NULL).
    
   - An MVszW value property that is set to an array of null-terminated Unicode character strings. For more information see the [SWStringArray](swstringarray.md) topic. 
    
> [!NOTE]
> The SPropValue is stored in a MAPI property in the PST's internal range. This property is inaccessible to ordinary MAPI applications. 
  
## Return value

S_OK 
  
> The function call was successful.
    
## Remarks

Persisted registrations may adversely affect the performance of applications, such as Outlook and Windows Desktop Search, that open PSTs. Consider the performance effect when using or expanding the usage of persisted registrations.
  
> [!IMPORTANT]
> This method is implemented for Unicode only. Further, it will preemptively fail if any of the paths in the array do not have a file name extension of .dll. 
  
## See also

- [IPSTOVERRIDE1 : IUnknown](ipstoverride1iunknown.md) 
- [IPSTOVERRIDEREQ : IUnknown](ipstoverridereqiunknown.md)

