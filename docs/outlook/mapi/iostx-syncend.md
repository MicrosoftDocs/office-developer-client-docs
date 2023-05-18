---
title: "IOSTXSyncEnd"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX.SyncEnd
api_type:
- COM
ms.assetid: da9de705-bdab-6cb8-35ea-61f03cdc4ff5
---

# IOSTX::SyncEnd

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Ends synchronization in the current state and exits that state.
  
```cpp
HRESULT SyncEnd();
```

## Remarks

The client must call **IOSTX::SyncEnd** for each call to [IOSTX::SyncBeg](iostx-syncbeg.md). The corresponding data structure holds information to indicate whether the client has successfully completed the current state so that Outlook can clean up its internal state.
  
## See also



[IOSTX::GetLastError](iostx-getlasterror.md)
  
[IOSTX::InitSync](iostx-initsync.md)
  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)
  
[IOSTX::SyncHdrEnd](iostx-synchdrend.md)
  
[IOSTX : IUnknown](iostxiunknown.md)


[MAPI Constants](mapi-constants.md)

