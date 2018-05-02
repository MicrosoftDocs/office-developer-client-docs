---
title: "IMAPIViewContextGetPrintSetup"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewContext.GetPrintSetup
api_type:
- COM
ms.assetid: eaf3bafb-975d-42c8-99ea-7f9ef9c934ba
description: "Last modified: July 23, 2011"
---

# IMAPIViewContext::GetPrintSetup

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Retrieves current printing information.
  
```
HRESULT GetPrintSetup(
ULONG ulFlags,
LPFORMPRINTSETUP FAR * lppFormPrintSetup
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags that controls the type of the returned strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lppFormPrintSetup_
  
> [out] Pointer to a pointer to a structure that holds the printing information.
    
## Return value

S_OK 
  
> The printing information was successfully retrieved.
    
## Remarks

Form objects call the **IMAPIViewContext::GetPrintSetup** method to retrieve information about the printer setup before attempting to print the current message. 
  
## Notes to Implementers

Allocate the **hDevMode** and **hDevName** members of the [FORMPRINTSETUP](formprintsetup.md) structure using the Win32 function **GlobalAlloc**.
  
## Notes to Callers

If you expect the **hDevMode** and **hDevName** members of the **FORMPRINTSETUP** structure pointed to by the  _lppFormPrintSetup_ parameter to be Unicode strings, set  _ulFlags_ to MAPI_UNICODE. Otherwise, **GetPrintSetup** will return these strings in ANSI format. 
  
Free the **hDevMode** and **hDevName** members of the **FORMPRINTSETUP** structure by calling the Win32 function **GlobalFree**. Free the entire **FORMPRINTSETUP** structure by calling [MAPIFreeBuffer](mapifreebuffer.md). 
  
## See also

#### Reference

[FORMPRINTSETUP](formprintsetup.md)
  
[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)

