---
title: "IPersistMessageGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.GetLastError
api_type:
- COM
ms.assetid: 32cc3a1f-1310-4788-b0f4-93c1e4940f37
description: "Last modified: July 23, 2011"
---

# IPersistMessage::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error in the form object. 
  
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
  
> The strings in the [MAPIERROR](mapierror.md) structure returned in the  _lppMAPIError_ parameter are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to a **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if the form cannot supply appropriate information for a **MAPIERROR** structure. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the address book provider does not support Unicode, or MAPI_UNICODE was not set and the address book provider supports only Unicode.
    
## Remarks

Form objects implement the **IPersistMessage::GetLastError** method to supply information about a prior method call that failed. Form viewers can provide their users with detailed information about the error by including the data from the [MAPIERROR](mapierror.md) structure in a dialog box. 
  
A call to **GetLastError** does not affect the state of the form. When **GetLastError** returns, the form remains in the state that it was in before the call was made. 
  
## Notes to callers

You can use the **MAPIERROR** structure, if the form supplies one, that is pointed to by the  _lppMAPIError_ parameter only if **GetLastError** returns S_OK. Sometimes the form cannot determine what the last error was or has nothing more to report about the error. In this situation, the form returns a pointer to NULL in  _lppMAPIError_ instead. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
## See also



[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IPersistMessage : IUnknown](ipersistmessageiunknown.md)

