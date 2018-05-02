---
title: "MSProviderInit"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MSProviderInit
api_type:
- HeaderDef
ms.assetid: 230c66c4-ab04-4fa6-946f-9f4b704f2842
description: "Last modified: March 09, 2015"
---

# MSProviderInit

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Initializes a message store provider for operation.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
   
```
HRESULT MSProviderInit(
  HINSTANCE hInstance,
  LPMALLOC lpMalloc,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPALLOCATEMORE lpAllocateMore,
  LPFREEBUFFER lpFreeBuffer,
  ULONG ulFlags,
  ULONG ulMAPIVer,
  ULONG FAR * lpulProviderVer,
  LPMSPROVIDER FAR * lppMSProvider
);
```

## Parameters

 _hInstance_
  
> [in] The instance of the message store provider's dynamic-link library (DLL) that MAPI used when it linked. 
    
 _lpMalloc_
  
> [in] Pointer to a memory allocator object exposing the OLE **IMalloc** interface. The message store provider may need to use this allocation method when working with certain interfaces such as **IStream**. 
    
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
  
> [in] Version number of the service provider interface (SPI) that MAPI uses. For the current version number, see the Mapispi.h header file. 
    
 _lpulProviderVer_
  
> [out] Pointer to the version number of the SPI that this message store provider uses. 
    
 _lppMSProvider_
  
> [out] Pointer to a pointer to the initialized message store provider object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_VERSION 
  
> The SPI version being used by MAPI is not compatible with the SPI being used by this provider.
    
## Remarks

MAPI calls the entry point function **MSProviderInit** to initialize a message store provider following a client logon. 
  
## Notes to Implementers

A message store provider must implement **MSProviderInit** as an entry point function in the provider's DLL. The implementation must be based on the **MSPROVIDERINIT** function prototype, also specified in MAPISPI.H. MAPI defines **MSPROVIDERINIT** to use the standard MAPI initialization call type, STDMAPIINITCALLTYPE, which causes **MSProviderInit** to follow the CDECL calling convention. An advantage of CDECL is that calls can be attempted even if the number of calling parameters does not match the number of defined parameters. 
  
A provider can be initialized multiple times, as a result of appearing in several profiles in simultaneous use or of appearing more than once in the same profile. Because the provider object contains context, **MSProviderInit** must return a different provider object in  _lppMSProvider_ for each initialization, even for multiple initializations in the same process. 
  
The provider DLL should not be linked with Mapix.dll. Instead, it should use these pointers for memory allocation or deallocation. 
  
The message store provider should use the functions pointed to by  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ for most memory allocation and deallocation. In particular, the provider must use these functions to allocate memory for use by client applications when calling object interfaces such as [IMAPIProp::GetProps](imapiprop-getprops.md) and [IMAPITable::QueryRows](imapitable-queryrows.md). If the provider also expects to use the OLE memory allocator, it should call the **IUnknown::AddRef** method of the allocator object pointed to by the  _lpMalloc_ parameter. 
  
For more information about writing **MSProviderInit**, see [Loading Message Store Providers](loading-message-store-providers.md). For more information about entry point functions, see [Implementing a Service Provider Entry Point Function](implementing-a-service-provider-entry-point-function.md). 
  
## See also

#### Reference

[ABProviderInit](abproviderinit.md)
  
[IMSProvider : IUnknown](imsprovideriunknown.md)
  
[XPProviderInit](xpproviderinit.md)

