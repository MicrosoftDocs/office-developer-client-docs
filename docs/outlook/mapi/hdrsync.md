---
title: "HDRSYNC"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: bf6892d0-a923-e926-5361-59efa49ebdc0
description: "Last modified: July 23, 2011"
---

# HDRSYNC

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Information for synchronizing a message header during the [download message header state](download-message-header-state.md).
  
## Quick info

```cpp
struct HDRSYNC 
{ 
    UPMSG *pupmsg; 
    FEID feidPar; 
    LPSTREAM pstmReserved; 
    ULONG ulFlags; 
    LPMESSAGE pmsgFull; 
};
```

## Members

 _pupmsg_
  
- [out] Information for the current message header in the local store.
    
 _feidPar_
  
- [out] Entry ID for the parent folder of the message item.
    
 _pstmReserved_
  
- [out] This member is reserved for the internal use of Outlook and is not supported. 
    
 _ulFlags_
  
- [in] Flags to modify behavior:
    
- HSF_LOCAL
    
  - [in] Full item resides in the same local store as the header item.
    
- HSF_COPYDESTRUCTIVE
    
  -  [in] Optimize internal copy operations. This might cause data loss. **HSF_LOCAL** must be set. 
    
- HSF_OK
    
  - [in] Header synchronization was successful. The client sets this after downloading information from the server.
    
     _pmsgFull_
    
  - [in] The full message item including the message header downloaded from the server. See mapidefs.h for the type definition of **LPMESSAGE**. 
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[MAPI Constants](mapi-constants.md)
  
[FEID](feid.md)

