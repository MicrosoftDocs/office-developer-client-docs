---
title: "IOSTXInitSync"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IOSTX.InitSync
api_type:
- COM
ms.assetid: e22244a2-ac5f-910a-501f-4483ea0667c2
description: "Last modified: July 23, 2011"
---

# IOSTX::InitSync

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Informs the local message store that synchronization is about to start.
  
```cpp
HRESULT InitSync( 
    ULONG ulFlags 
);
```

## Parameters

 _ulFlags_
  
> [in] Flags to determine appropriate behavior during synchronization. Outlook uses these flags in each state of the replication state machine to determine the information that it should provide for the client. For example, if the client passes **SYNC_ONLY_ASSOCIATED**, Outlook will only return information related to associated (or hidden) items. 
    
## See also



[IOSTX::GetLastError](iostx-getlasterror.md)
  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncEnd](iostx-syncend.md)
  
[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)
  
[IOSTX::SyncHdrEnd](iostx-synchdrend.md)
  
[IOSTX : IUnknown](iostxiunknown.md)


[MAPI Constants](mapi-constants.md)

