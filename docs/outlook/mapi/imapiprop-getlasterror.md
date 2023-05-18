---
title: "IMAPIPropGetLastError"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.GetLastError
api_type:
- COM
ms.assetid: f64a765d-c653-4eef-a0fc-24a54968757c
---

# IMAPIProp::GetLastError

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error. 
  
```cpp
HRESULT GetLastError(
  HRESULT hResult,
  ULONG ulFlags,
  LPMAPIERROR FAR * lppMAPIError
);
```

## Parameters

 _hResult_
  
> [in] A handle to the error code generated in the previous method call.
    
 _ulFlags_
  
> [in] A bitmask of flags that indicates the format for the text returned in the **MAPIERROR** structure pointed to by  _lppMAPIError_. The following flag can be set:
    
MAPI_UNICODE 
  
> The strings should be in Unicode format. If the MAPI_UNICODE flag is not set, the strings should be in ANSI format.
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the **MAPIERROR** structure that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if there is no error information to return. 
    
## Return value

S_OK 
  
> The error information was returned.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

The **IMAPIProp::GetLastError** method supplies information about a prior method call that failed. Clients can provide their users with detailed information about the error by including the data from the **MAPIERROR** structure in a dialog box. 
  
All of the implementations of **GetLastError** provided by MAPI are ANSI implementations, except for the [IAddrBook](iaddrbookimapiprop.md) implementation. The **GetLastError** method included with **IAddrBook** supports Unicode. 
  
## Notes to implementers

The details of a remote transport provider's implementation of this method and what messages this method returns are up to the transport provider, because the particular error conditions that lead to various HRESULT values will be different for different transport providers.
  
## Notes to callers

You can use the **MAPIERROR** structure pointed to by the  _lppMAPIError_ parameter, if **GetLastError** supplies one, only if the return value is S_OK. Sometimes **GetLastError** cannot determine what the last error was or has nothing more to report about the error. In this situation, a pointer to NULL is returned in  _lppMAPIError_ instead. 
  
To release the memory for the **MAPIERROR** structure, call the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
For more information about the **GetLastError** method, see [MAPI Extended Errors](mapi-extended-errors.md).
  
## See also



[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)
  
[MAPIERROR](mapierror.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MAPI Extended Errors](mapi-extended-errors.md)

