---
title: "OLFI"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 44bfaadf-36f9-bd8e-6158-646533f6849e
description: "Last modified: July 23, 2011"
---

# OLFI

  
  
**Applies to**: Outlook 
  
Queue of long-term ID structures used by the Personal Folders file (PST) store provider to assign an Entry ID for a new message or folder in offline mode.
  
## Quick Info

```
typedef struct { 
    ULONG    ulVersion; 
    MAPIUID  muidReserved; 
    ULONG    ulReserved; 
    DWORD    dwAlloc; 
    DWORD    dwNextAlloc; 
    LTID     ltidAlloc; 
    LTID     ltidNextAlloc; 
} OLFI, *POLFI;
```

## Members

 _ulVersion_
  
- Version number for the structure. 
    
 _muidReserved_
  
- This member is reserved for the internal use of Outlook and is not supported.
    
 _ulReserved_
  
- This member is reserved for the internal use of Outlook and is not supported.
    
 _dwAlloc_
  
- The number of entries that are available for allocation. These entries share the same globally unique identifier (GUID).
    
 _dwNextAlloc_
  
- The number of entries that are available next for allocation. These entries share the same GUID.
    
 _ltidAlloc_
  
- The long-term ID structure, **[LTID](ltid.md)**, identifying the entry currently available for allocation. The long-term ID structure contains a GUID and an index identifying an object in the store. Together, the GUID and the index can form a unique Entry ID for an object. 
    
 _ltidNextAlloc_
  
- Long-term ID structure identifying the next available entry.
    
## Remarks

An Entry ID is a 4-byte MAPI entry identifier for a folder or a message. For more information, see [ENTRYID](http://msdn.microsoft.com/en-us/library/ms836424).
  
When a PST store provider assigns an Entry ID to a new object, it first needs a GUID that identifies the server, and an index that identifies the object in the store. Even though the GUID is not unique across all Entry IDs, the GUID and the index combined provide a unique entry. This GUID and index pair is tracked by a long-term ID structure, **LTID**, which is part of the **OLFI** structure. 
  
The PST store provider does not physically keep in **OLFI** an **LTID** structure for each GUID-index pair. It keeps one **LTID** structure,  *ltidAlloc*  , for the currently first available GUID-index pair; a count,  *dwAlloc*  , of the number of available entries that share this same GUID; and a second **LTID** structure,  *ltidNextAlloc*  , for the next available GUID-index pair that has a different GUID. The PST store provider uses the **OLFI** structure to track the GUIDs and indexes that it has handed out. At a virtual level, the provider maintains a reserve of a number of **LTID** structures that are ready to be allocated.  *dwAlloc*  maintains a count of the available **LTID** structures. 
  
Requests for Entry IDs come in blocks. When there is a request for a block, the PST store provider checks if there is sufficient reserve on hand by comparing the requested size with  *dwAlloc*  . If there is sufficient reserve, it returns the GUID and index in  *ltidAlloc*  for allocation. It then decreases  *dwAlloc*  by the requested size, and increments the index in  *ltidAlloc*  by the requested size. This prepares the PST store provider to allocate  *ltidAlloc*  on the next request for another block of Entry IDs. Note that the GUID remains the same for the next request. 
  
If the size of a request is larger than  *dwAlloc*  , the PST store provider tries to use what it has next in reserve, as specified by  *dwNextAlloc*  and  *ltidNextAlloc*  . It copies  *dwNextAlloc*  and  *ltidNextAlloc*  to  *dwAlloc*  and  *ltidAlloc*  respectively, and sets  *dwNextAlloc*  and  *ltidNextAlloc*  to NULL. 
  
A provider that wraps the PST store provider should periodically check  *ltidNextAlloc*  to see if it is NULL. If it is, the provider should populate it with a new GUID and reset  *dwNextAlloc*  so that more entry IDs can be allocated. 
  
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[LTID](ltid.md)

