---
title: "ABProviderInit"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ABProviderInit
api_type:
- HeaderDef
ms.assetid: c3dcd0d4-018a-47b0-b040-227034ed59d8
description: "Last modified: March 09, 2015"
---

# ABProviderInit
 
**Applies to**: Outlook 
  
Initializes an address book provider for operation. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Implemented by:  <br/> |Address book providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
   
```cpp
HRESULT ABProviderInit(
  HINSTANCE hInstance,
  LPMALLOC lpMalloc,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPALLOCATEMORE lpAllocateMore,
  LPFREEBUFFER lpFreeBuffer,
  ULONG ulFlags,
  ULONG ulMAPIVer,
  ULONG FAR * lpulProviderVer,
  LPABPROVIDER FAR * lppABProvider
);
```

## Parameters

 _hInstance_
  
> [in] The instance of the address book provider's dynamic-link library (DLL) that MAPI used when it linked. 
    
 _lpMalloc_
  
> [in] Pointer to a memory allocator object exposing the OLE **IMalloc** interface. The address book provider may need to use this allocation method when working with certain interfaces such as **IStream**. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used where required by MAPI to allocate memory. 
    
 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used where required by MAPI to allocate additional memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used where required by MAPI to free memory. 
    
 _ulFlags_
  
> [in] Bitmask of flags. The following flag can be set:
    
MAPI_NT_SERVICE 
  
> The provider is being loaded in the context of a Windows service, a special type of process without access to any user interface. 
    
 _ulMAPIVer_
  
> [in] Version number of the service provider interface (SPI) that MAPI.DLL uses. For the current version number, see the MAPISPI.H header file. 
    
 _lpulProviderVer_
  
> [out] Pointer to the version number of the SPI that this address book provider uses. 
    
 _lppABProvider_
  
> [out] Pointer to a pointer to the initialized address book provider object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_VERSION 
  
> The SPI version being used by MAPI is not compatible with the SPI being used by this provider.
    
## Remarks

MAPI calls the entry point function **ABProviderInit** to initialize an address book provider following a client logon. 
  
## Notes to implementers

An address book provider must implement **ABProviderInit** as an entry point function in the provider's DLL. The implementation must be based on the **ABPROVIDERINIT** function prototype, also specified in MAPISPI.H. MAPI defines **ABPROVIDERINIT** to use the standard MAPI initialization call type, STDMAPIINITCALLTYPE, which causes **ABProviderInit** to follow the CDECL calling convention. 
  
A provider can be initialized multiple times, as a result of appearing in several profiles in simultaneous use or of appearing more than once in the same profile. Because the provider object contains context, **ABProviderInit** must return a different provider object in  _lppABProvider_ for each initialization, even for multiple initializations in the same process. 
  
The address book provider should use the functions pointed to by  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ for most memory allocation and deallocation. In particular, the provider must use these functions to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md). If the provider also expects to use the OLE memory allocator, it should call the **IUnknown::AddRef** method of the allocator object pointed to by the  _lpMalloc_ parameter. 
  
For more information on writing **ABProviderInit**, see [Implementing an Address Book Provider Entry Point Function](implementing-an-address-book-provider-entry-point-function.md). For more information on entry point functions, see [Implementing a Service Provider Entry Point Function](implementing-a-service-provider-entry-point-function.md). 
  
## See also

- [IABProvider : IUnknown](iabprovideriunknown.md) 
- [MSProviderInit](msproviderinit.md)
- [XPProviderInit](xpproviderinit.md)

