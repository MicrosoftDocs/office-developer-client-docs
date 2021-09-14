---
title: "IMAPISupportGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.GetLastError
api_type:
- COM
ms.assetid: 5b4290d9-230f-416a-9644-188578565c7b
description: "Last modified: July 23, 2011"
---

# IMAPISupport::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous support object error. 
  
```cpp
HRESULT GetLastError(
  HRESULT hResult,
  ULONG ulFlags,
  LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] A handle to the error value generated in the previous method call for the support object.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if a **MAPIERROR** structure with appropriate error information cannot be provided. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and MAPI does not support Unicode, or MAPI_UNICODE was not set and MAPI supports only Unicode.
    
## Remarks

The **IMAPISupport::GetLastError** method is implemented for all support objects. Callers can provide their users with detailed information about the error by including the data from the **MAPIERROR** structure in a dialog box. 
  
## Notes to callers

You can use the pointer to the **MAPIERROR** structure, if MAPI supplies one, in the  _lppMAPIError_ parameter only if **GetLastError** returns S_OK. Sometimes MAPI cannot determine what the last error was or it has nothing more to report about the error. In this situation,  _lppMAPIError_ returns a pointer to NULL instead. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
To release all the memory allocated by MAPI, call the [MAPIFreeBuffer](mapifreebuffer.md) function for the returned **MAPIERROR** structure. 
  
## See also



[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)


[MAPI Extended Errors](mapi-extended-errors.md)

