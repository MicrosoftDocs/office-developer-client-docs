---
title: "IOSTXSyncHdrEnd"
description: "Describes the syntax, parameters, and remarks for IOSTX SyncHdrEnd, which ends synchronization for a message header."
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX.SyncHdrEnd
api_type:
- COM
ms.assetid: a0beb6eb-7978-c64e-dba1-89f0caf2090e
---

# IOSTX::SyncHdrEnd

**Applies to**: Outlook 2013 | Outlook 2016
  
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

Upon **[IOSTX::SyncBeg](iostx-syncbeg.md)**, the local store enters the [download message header state](download-message-header-state.md). The client downloads a full message item (as _pmsgFull_ in **[HDRSYNC](hdrsync.md)** ). If this is successful, the client also sets _ulFlags_ in **HDRSYNC** as **HSF_OK**. Upon **IOSTX::SyncHdrEnd**, Outlook checks the result in **HDRSYNC** and uses _pprog_ and the information in **HDRSYNC** to update the local message header.
  
The local store returns to the state it was in before the preceding **[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)**.
  
## See also

[IOSTX::GetLastError](iostx-getlasterror.md)  
[IOSTX::InitSync](iostx-initsync.md)  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)  
[IOSTX::SyncBeg](iostx-syncbeg.md)  
[IOSTX::SyncEnd](iostx-syncend.md)  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)  
[IOSTX : IUnknown](iostxiunknown.md)
[MAPI Constants](mapi-constants.md)
