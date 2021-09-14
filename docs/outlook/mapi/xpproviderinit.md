---
title: "XPProviderInit"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.XPProviderInit
api_type:
- COM
ms.assetid: df6eacf4-1cf9-4c25-806f-f87c38dad597
description: "Last modified: March 09, 2015"
---

# XPProviderInit

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initializes a transport provider for operation.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Implemented by:  <br/> |Transport providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
   
```cpp
HRESULT XPProviderInit(
  HINSTANCE hInstance,
  LPMALLOC lpMalloc,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPALLOCATEMORE lpAllocateMore,
  LPFREEBUFFER lpFreeBuffer,
  ULONG ulFlags,
  ULONG ulMAPIVer,
  ULONG FAR * lpulProviderVer,
  LPXPPROVIDER FAR * lppXPProvider
);
```

## Parameters

 _hInstance_
  
> [in] The instance of the transport provider's dynamic-link library (DLL) that MAPI used when it loaded the DLL.
    
 _lpMalloc_
  
> [in] Pointer to a memory allocator object exposing the OLE **IMalloc** interface. The transport provider may need to use this allocation method when working with certain interfaces such as **IStream**. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory. 
    
 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory. 
    
 _ulFlags_
  
> [in] Bitmask of flags. The following flag can be set:
    
MAPI_NT_SERVICE 
  
> The provider is being loaded in the context of a Windows service, a special type of process without access to any user interface. 
    
 _ulMAPIVer_
  
> [in] Version number of the service provider interface (SPI) that Mapi.dll uses. For the current version number, see the Mapispi.h header file. 
    
 _lpulProviderVer_
  
> [out] Pointer to the version number of the SPI that this transport provider uses. 
    
 _lppXPProvider_
  
> [out] Pointer to a pointer to the initialized transport provider object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_VERSION 
  
> The SPI version being used by MAPI is not compatible with the SPI being used by this provider.
    
## Remarks

MAPI calls the entry point function **XPProviderInit** to initialize a transport provider following a client logon. **XPProviderInit** is called once for each transport provider specified in the client's profile. 
  
## Notes to implementers

A transport provider must implement **XPProviderInit** as an entry point function in the provider's DLL. The implementation must be based on the **XPPROVIDERINIT** function prototype, also specified in Mapispi.h. MAPI defines **XPPROVIDERINIT** to use the standard MAPI initialization call type, STDMAPIINITCALLTYPE, which causes **XPProviderInit** to follow the CDECL calling convention. An advantage of CDECL is that calls can be attempted even if the number of calling parameters does not match the number of defined parameters. 
  
A provider can be initialized multiple times as a result of appearing in several profiles in simultaneous use or of appearing more than once in the same profile. Because the provider object contains context, **XPProviderInit** must return a different provider object in  _lppXPProvider_ for each initialization, even for multiple initializations in the same process. 
  
The transport provider should use the functions pointed to by  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ for most memory allocation and deallocation. In particular, the provider must use these functions to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md). If the provider also expects to use the OLE memory allocator, it should call the **IUnknown::AddRef** method of the allocator object pointed to by the  _lpMalloc_ parameter. 
  
For more information about writing **XPProviderInit**, see [Initializing the Transport Provider](initializing-the-transport-provider.md). For more information about entry point functions, see [Implementing a Service Provider Entry Point Function](implementing-a-service-provider-entry-point-function.md). 
  
## See also



[ABProviderInit](abproviderinit.md)
  
[IXPProvider : IUnknown](ixpprovideriunknown.md)
  
[MSProviderInit](msproviderinit.md)

