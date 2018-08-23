---
title: "IMAPIViewContextGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewContext.GetLastError
api_type:
- COM
ms.assetid: 3306e37a-2500-4281-96c3-ca0d5c81909d
description: "Last modified: July 23, 2011"
---

# IMAPIViewContext::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the view context object. 
  
```cpp
HRESULT GetLastError(
HRESULT hResult,
ULONG ulFlags,
LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] HRESULT data type that contains the error value generated in the previous method call.
    
 _ulFlags_
  
> [in] Bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] Pointer to a pointer to the returned **MAPIERROR** structure that contains version, component, and context information for the error. This parameter can be set to NULL if there is no **MAPIERROR** structure to return. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and **GetLastError** does not support Unicode, or MAPI_UNICODE was not set and **GetLastError** only supports Unicode. 
    
## Remarks

The **IMAPIViewContext::GetLastError** method supplies information about a prior method call that failed. Callers can provide their users with detailed information about the error by including the data from the **MAPIERROR** structure in a dialog box. 
  
## Notes to callers

You can make use of the **MAPIERROR** structure pointed to by the  _lppMAPIError_ parameter if MAPI supplies one only if **GetLastError** returns S_OK. Sometimes MAPI cannot determine what the last error was or has nothing more to report about the error. In this situation, a pointer to NULL is returned in  _lppMAPIError_ instead. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
## See also



[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)

