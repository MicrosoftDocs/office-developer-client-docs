---
title: "IMAPISupportGetMemAllocRoutines"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.GetMemAllocRoutines
api_type:
- COM
ms.assetid: 52d45876-367b-42da-b99a-29cdb71fa5a9
description: "Last modified: July 23, 2011"
---

# IMAPISupport::GetMemAllocRoutines

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the addresses of the MAPI memory allocation and deallocation functions ([MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md)).
  
```cpp
HRESULT GetMemAllocRoutines(
  LPALLOCATEBUFFER FAR * lppAllocateBuffer,
  LPALLOCATEMORE FAR * lppAllocateMore,
  LPFREEBUFFER FAR * lppFreeBuffer
);
```

## Parameters

 _lppAllocateBuffer_
  
> [out] A pointer to a pointer to the **MAPIAllocateBuffer** function. **MAPIAllocateBuffer** allocates memory. 
    
 _lppAllocateMore_
  
> [out] A pointer to a pointer to the **MAPIAllocateMore** function. **MAPIAllocateMore** allocates additional memory for memory that was originally allocated by using **MAPIAllocateBuffer**.
    
 _lppFreeBuffer_
  
> [out] A pointer to a pointer to the **MAPIFreeBuffer** function. **MAPIFreeBuffer** frees memory. 
    
## Return value

S_OK 
  
> The function addresses were successfully returned.
    
## Remarks

The **IMAPISupport::GetMemAllocRoutines** method is implemented for all support objects. Service providers call **GetMemAllocRoutines** to get the addresses of the three memory allocation functions that are passed to their initialization function ( [ABProviderInit](abproviderinit.md), [MSProviderInit](msproviderinit.md), or [XPProviderInit](xpproviderinit.md)). 
  
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIAllocateMore](mapiallocatemore.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

