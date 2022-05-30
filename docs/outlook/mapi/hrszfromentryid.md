---
title: "HrSzFromEntryID"
description: Describes HrSzFromEntryID provides syntax, parameters, and return value.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrSzFromEntryID
api_type:
- COM
ms.assetid: 5e3ed6b2-8eaf-44ab-bc6a-d3faabe84a93
---

# HrSzFromEntryID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Encodes an entry identifier into an ASCII string. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HrSzFromEntryID(
  ULONG cb,
  LPENTRYID pentry,
  LPSTR FAR * psz
);
```

## Parameters

 _cb_
  
> [in] Size, in bytes, of the entry identifier pointed to by the  _pentry_ parameter. 
    
 _pentry_
  
> [in] Pointer to an [ENTRYID](entryid.md) structure that contains the entry identifier to be encoded. 
    
 _psz_
  
> [out] Pointer to the returned ASCII string.
    
## Return value

None.
  
## Remarks

The [HrEntryIDFromSz](hrentryidfromsz.md) and **HrSzFromEntryID** functions provide conversion between the string and binary formats of entry identifiers. With MAPI, you should use structures with binary data. 
  
## Notes to callers

The **HrSzFromEntryID** function allocates memory for the ASCII string using the [MAPIAllocateBuffer](mapiallocatebuffer.md) function. 
  

