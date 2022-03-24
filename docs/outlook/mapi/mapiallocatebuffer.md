---
title: "MAPIAllocateBuffer"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPIAllocateBuffer
api_type:
- HeaderDef
ms.assetid: f1fc7fc5-c71f-44f7-930a-571773eb6809
description: "Last modified: March 09, 2015"
---

# MAPIAllocateBuffer

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Allocates a memory buffer. 
  
|Property|Description|
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE MAPIAllocateBuffer(
  ULONG cbSize,
  LPVOID FAR * lppBuffer
);
```

## Parameters

 _cbSize_
  
> [in] Size, in bytes, of the buffer to be allocated. 
    
 _lppBuffer_
  
> [out] Pointer to the returned allocated buffer.
    
## Return value

S_OK 
  
> The call succeeded and has returned the requested memory buffer.
    
## Remarks

During **MAPIAllocateBuffer** call processing, the calling implementation acquires a block of memory from the operating system. The memory buffer is allocated on an even-numbered byte address. On platforms where long integer access is more efficient, the operating system allocates the buffer on an address whose size in bytes is a multiple of four. 
  
Calling the [MAPIFreeBuffer](mapifreebuffer.md) function releases the memory buffer allocated by **MAPIAllocateBuffer**, by calling the [MAPIAllocateMore](mapiallocatemore.md) function and any buffers linked to it, when the memory is no longer needed. 
  
## See also



[MAPIReallocateBuffer](mapireallocatebuffer.md)

