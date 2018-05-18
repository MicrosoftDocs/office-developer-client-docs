---
title: "IPSTXEmulateSpooler"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPSTX.EmulateSpooler
api_type:
- COM
ms.assetid: aec72e51-1f75-b2c5-76ca-626cd21fbc7d
description: "Last modified: July 23, 2011"
---

# IPSTX::EmulateSpooler

  
  
**Applies to**: Outlook 
  
Sets a local store to emulate the Outlook Protocol Manager to spool outgoing messages to a server.
  
```cpp
HRESULT EmulateSpooler( 
    BOOL fEmulate 
);
```

 _fEmulate_
  
>  [in] Set this parameter to True if the local store should emulate the spooler; set it to False if not. 
    
## Remarks

A local store calls **IPSTX::EmulateSpooler** to act as an Outlook Protocol Manager, spooling messages in the outgoing queue to the back-end server (for example, MSN server or AOL server) for processing. Emulating a spooler during synchronization, the store then calls these two methods: 
  
1. **[IMsgStore::GetOutgoingQueue](imsgstore-getoutgoingqueue.md)** to get the outgoing queue of messages in the store. This method succeeds only if the store is emulating the Outlook Protocol Manager. 
    
2. **[IMsgStore::SetLockState](imsgstore-setlockstate.md)** to secure sole access to a message in the outgoing queue just before sending it to the server. This method succeeds only if the store is emulating the Outlook Protocol Manager. After sending the message, the store calls this method again to release sole access to it. 
    
> [!NOTE]
> Since Outlook 2002, the Outlook Protocol Manager replaced the MAPI spooler and became responsible for spooling outgoing messages to back-end servers. 
  
## See also



[IPSTX::GetLastError](ipstx-getlasterror.md)
  
[IPSTX::GetSyncObject](ipstx-getsyncobject.md)

