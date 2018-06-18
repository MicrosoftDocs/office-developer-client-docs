---
title: "IMSLogonGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSLogon.GetLastError
api_type:
- COM
ms.assetid: 3e296f6d-4833-4c68-9b84-df0b09878474
description: "Last modified: July 23, 2011"
---

# IMSLogon::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the last error that occurred for the message store object. 
  
```cpp
HRESULT GetLastError(
  HRESULT hResult,
  ULONG ulFlags,
  LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] An HRESULT data type that contains the error value generated in the previous method call for the message store object.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the returned **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if there is no **MAPIERROR** to return. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

Use the **IMSLogon::GetLastError** method to retrieve information to display in a message to the user regarding the last error returned from a method call for the message store object. 
  
To release all the memory allocated by MAPI for the returned **MAPIERROR** structure, client applications need to call only the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
The return value from **GetLastError** must be S_OK for an application to use the **MAPIERROR**. Even if the return value is S_OK, a **MAPIERROR** might not be returned. If the implementation cannot determine what the last error was, or if a **MAPIERROR** is not available for that error, **GetLastError** returns a pointer to NULL in  _lppMAPIError_ instead. 
  
## See also



[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

