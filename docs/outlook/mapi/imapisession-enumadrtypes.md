---
title: "IMAPISessionEnumAdrTypes"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.EnumAdrTypes
api_type:
- COM
ms.assetid: 9a3702a4-8a6b-4c0c-a90f-02be3a2bfa05
description: "Last modified: July 23, 2011"
---

# IMAPISession::EnumAdrTypes

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Deprecated. Returns the address types that can be handled by all of the transport providers in the session. 
  
```cpp
HRESULT EnumAdrTypes(
  ULONG ulFlags,
  ULONG FAR * lpcAdrTypes,
  LPSTR FAR * FAR * lpppszAdrTypes
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that indicates the format for the returned address types. The following flag can be set:
    
MAPI_UNICODE 
  
> The address types are in Unicode format. If the MAPI_UNICODE flag is not set, the address types are in ANSI format.
    
 _lpcAdrTypes_
  
> [out] A pointer to a count of address types pointed to by the  _lpppszAdrTypes_ parameter. 
    
 _lpppszAdrTypes_
  
> [out] A pointer to an array of pointers to address types.
    
## Return value

S_OK 
  
> The address types were successfully retrieved.
    
## Remarks

The **IMAPISession::EnumAdrTypes** method returns a list of the address types that can be handled by all of the active transport providers in the session. The address types for transport providers that are not currently loaded are not included in the list. Transport providers register to handle one or more address types when MAPI calls their [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method. 
  
## Notes to callers

Call [MAPIFreeBuffer](mapifreebuffer.md) to release the string array pointed to by the  _lpppszAdrTypes_ parameter. 
  
## See also



[IXPLogon::AddressTypes](ixplogon-addresstypes.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)

