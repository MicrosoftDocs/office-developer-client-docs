---
title: "IProviderAdminGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin.GetLastError
api_type:
- COM
ms.assetid: 853ddee5-24d6-423d-b483-6a07a12de51f
description: "Last modified: July 23, 2011"
---

# IProviderAdmin::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error that occurred to the provider administration object. 
  
```cpp
HRESULT GetLastError(
  HRESULT hResult,
  ULONG ulFlags,
  LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] An HRESULT data type that contains the error value generated in the previous method call.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the returned **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if there is no **MAPIERROR** to return. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **GetLastError** does not support Unicode, or MAPI_UNICODE was not set and **GetLastError** supports only Unicode. 
    
## Remarks

The **IProviderAdmin::GetLastError** method supplies information about a prior method call that failed. Callers can provide their users with detailed information about the error by including the data from the **MAPIERROR** structure in a dialog box. 
  
## Notes to callers

You can use the **MAPIERROR** structure, if MAPI supplies one, that the  _lppMAPIError_ parameter points to only if **GetLastError** returns S_OK. Sometimes MAPI cannot determine what the last error was or has nothing more to report about the error. In this situation, a pointer to NULL is returned in  _lppMAPIError_ instead. 
  
For more information about the **GetLastError** method, see [Using Extended Errors](mapi-extended-errors.md).
  
## See also



[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IProviderAdmin : IUnknown](iprovideradminiunknown.md)

