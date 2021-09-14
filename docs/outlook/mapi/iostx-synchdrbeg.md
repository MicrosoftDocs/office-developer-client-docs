---
title: "IOSTXSyncHdrBeg"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX.SyncHdrBeg
api_type:
- COM
ms.assetid: 7f8ca7cf-ac0b-9b77-c1dd-9f1d0871d603
description: "Last modified: July 23, 2011"
---

# IOSTX::SyncHdrBeg

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Starts synchronization for a message header.
  
```cpp
HRESULT SyncHdrBeg( 
    ULONG cbeid, 
    LPENTRYID lpeid, 
    LPVOID *ppv 
);
```

## Parameters

 _cbeid_
  
> [in] The number of bytes in the entry ID for the message.
    
 _lpeid_
  
> [in] The entry ID for the message.
    
 _ppv_
  
>  [in]/[out] Pointer to the **[HDRSYNC](hdrsync.md)** structure for the message header. 
    
## Remarks

Upon **IOSTX::SyncHdrBeg**, the local store transitions to the [download message header state](download-message-header-state.md). Outlook initializes for the client the **HDRSYNC** structure with the current representation of the message header in the store and the parent folder. The client must then download a full message item (as  *pmsgFull*  in **HDRSYNC** ). If this was successful, the client also sets  *ulFlags*  in **HDRSYNC** as **HSF_OK**. Upon **[IOSTX::SyncHdrEnd](iostx-synchdrend.md)**, Outlook checks the result in **HDRSYNC** and uses the information in **HDRSYNC** to update the local message header. 
  
## See also



[IOSTX::GetLastError](iostx-getlasterror.md)
  
[IOSTX::InitSync](iostx-initsync.md)
  
[IOSTX::SetSyncResult](iostx-setsyncresult.md)
  
[IOSTX::SyncBeg](iostx-syncbeg.md)
  
[IOSTX::SyncEnd](iostx-syncend.md)
  
[IOSTX::SyncHdrEnd](iostx-synchdrend.md)
  
[IOSTX : IUnknown](iostxiunknown.md)


[MAPI Constants](mapi-constants.md)

