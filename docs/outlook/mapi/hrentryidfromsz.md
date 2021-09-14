---
title: "HrEntryIDFromSz"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrEntryIDFromSz
api_type:
- COM
ms.assetid: 14c171ec-0aec-43ab-8be8-e6bc0ce28a58
description: "Last modified: March 09, 2015"
---

# HrEntryIDFromSz

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Recreates an entry identifier from its ASCII encoding. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HRESULT HrEntryIDFromSz(
  LPSTR sz,
  ULONG FAR * pcb,
  LPENTRYID FAR * ppentry
);
```

## Parameters

 _sz_
  
> [in] Pointer to the ASCII string from which to create an entry identifier. 
    
 _pcb_
  
> [out] Pointer to the size, in bytes, of the entry identifier pointed to by the  _ppentry_ parameter. 
    
 _ppentry_
  
> [out] Pointer to a pointer to the returned [ENTRYID](entryid.md) structure that contains the new entry identifier. 
    
## Return value

S_OK
  
> The recreation was successful.
    
MAPI_E_INVALID_ENTRYID
  
> The entry ID was invalid.
    
## Remarks

The **HrEntryIDFromSz** and [HrSzFromEntryID](hrszfromentryid.md) functions provide conversion between the string and binary formats of entry identifiers. 
  
## Notes to callers

The **HrEntryIDFromSz** function allocates memory for the ASCII string using the [MAPIAllocateBuffer](mapiallocatebuffer.md) function. 
  

