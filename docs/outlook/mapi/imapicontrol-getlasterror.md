---
title: "IMAPIControlGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIControl.GetLastError
api_type:
- COM
ms.assetid: 83290b8e-fffc-41c8-a01e-578d130b65c5
description: "Last modified: July 23, 2011"
---

# IMAPIControl::GetLastError

  
  
**Applies to**: Outlook 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous button control error. 
  
```
HRESULT GetLastError(
  HRESULT hResult,
  ULONG ulFlags,
  LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] A handle to the error value generated in the previous method call.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the strings returned. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings in the **MAPIERROR** structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to a **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if the provider cannot supply a **MAPIERROR** structure with appropriate information. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

Service providers implement the **IMAPIControl::GetLastError** method to supply information about a prior method call that failed. MAPI can give users detailed information about the error by displaying the data from the **MAPIERROR** structure in a message or dialog box. 
  
## Notes to Implementers

You do not need to have information to include in the **MAPIERROR** structure for every error. It may not be possible to determine what the previous error was. If you have information, return S_OK and the appropriate data in the **MAPIERROR** structure. If no information is available, return S_OK and a pointer to NULL for the  _lppMAPIError_ parameter. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
## See also

#### Reference

[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPIControl : IUnknown](imapicontroliunknown.md)

