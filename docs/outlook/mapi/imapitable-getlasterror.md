---
title: "IMAPITableGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPITable.GetLastError
api_type:
- COM
ms.assetid: 832e2c18-ddba-4d18-a391-710d21fe23e6
description: "Last modified: July 23, 2011"
---

# IMAPITable::GetLastError

  
  
**Applies to**: Outlook 
  
Returns a [MAPIERROR](mapierror.md) structure containing information about the previous error on the table. 
  
```cpp
HRESULT GetLastError(
HRESULT hResult,
ULONG ulFlags,
LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] HRESULT containing the error generated in the previous method call.
    
 _ulFlags_
  
> [in] Bitmask of flags that controls the type of the returned strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] Pointer to a pointer to the returned **MAPIERROR** structure containing version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if a **MAPIERROR** structure with appropriate information cannot be provided. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation only supports Unicode.
    
## Remarks

The **IMAPITable::GetLastError** method returns detailed information, if available, about a prior method call that failed. This information can be displayed in a message or a dialog box. 
  
## Notes to Callers

Call **GetLastError** whenever you need to display information about an error to the user. 
  
You can make use of the [MAPIERROR](mapierror.md) structure pointed to by the  _lppMAPIError_ parameter if the table object supplies one only if **GetLastError** returns S_OK. Sometimes the table implementation cannot determine what the last error was or has nothing more to report about the error. In this situation, the pointer at  _lppMAPIError_ is set to NULL. 
  
To release all the memory allocated for the **MAPIERROR** structure, call the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
## See also

#### Reference

[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)

