---
title: "IOSTXSetSyncResult"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX.SetSyncResult
api_type:
- COM
ms.assetid: 7f083ee0-bf36-0059-1589-66e454fe0098
description: "Last modified: July 23, 2011"
---

# IOSTX::SetSyncResult

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the result of the synchronization.
  
```cpp
HRESULT SetSyncResult( 
    HRESULT hrSync 
);
```

## Parameters

 _hrSync_
  
> [in] The result of the synchronization. 
    
## Remarks

Call **IOSTX::SetSyncResult** before calling **IOSTX::SyncEnd** to inform the local store of the result of synchronization. 
  
## See also



[IOSTX::GetLastError](iostx-getlasterror.md)
  
[IOSTX::InitSync](iostx-initsync.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncEnd](iostx-syncend.md)
  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)
  
[IOSTX::SyncHdrEnd](iostx-synchdrend.md)


[MAPI Constants](mapi-constants.md)

