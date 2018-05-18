---
title: "IOSTXSyncHdrEnd"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IOSTX.SyncHdrEnd
api_type:
- COM
ms.assetid: a0beb6eb-7978-c64e-dba1-89f0caf2090e
description: "Last modified: July 03, 2012"
---

# IOSTX::SyncHdrEnd

 
  
**Applies to**: Outlook 
  
Ends synchronization for a message header.
  
```cpp
HRESULT SyncHdrEnd( 
    LPMAPIPROGRESS pprog 
);
```

## Parameters

 _pprog_
  
> [in] **[IMAPIProgress](imapiprogressiunknown.md)** interface for synchronization of moved or copied messages. See mapidefs.h for the type definition of **LPMAPIPROGRESS**. 
    
## Remarks

Upon **[IOSTX::SyncBeg](iostx-syncbeg.md)**, the local store enters the [download message header state](download-message-header-state.md). The client downloads a full message item (as  *pmsgFull*  in **[HDRSYNC](hdrsync.md)** ). If this is successful, the client also sets  *ulFlags*  in **HDRSYNC** as **HSF_OK**. Upon **IOSTX::SyncHdrEnd**, Outlook checks the result in **HDRSYNC** and uses  *pprog*  and the information in **HDRSYNC** to update the local message header. 
  
The local store returns to the state it was in before the preceding **[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)**. 
  
## See also

#### Reference

[IOSTX::GetLastError](iostx-getlasterror.md)
  
[IOSTX::InitSync](iostx-initsync.md)
  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncEnd](iostx-syncend.md)
  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)
  
[IOSTX : IUnknown](iostxiunknown.md)
#### Concepts

[MAPI Constants](mapi-constants.md)

