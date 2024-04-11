---
title: "IOSTX  IUnknown"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IOSTX
api_type:
- COM
ms.assetid: f374d8d9-be8e-2489-d5fe-8a92e0ecfc6f
description: "Provides synchronization methods. This interface retrieves necessary information to replicate local changes to the server and server changes to the local store."
---

# IOSTX : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides synchronization methods. This interface retrieves the necessary information to replicate local changes to the server and server changes to the local store.
  
|Property |Value |
|:-----|:-----|
|Provided by:  <br/> |[IPSTX::GetSyncObject](iostx-setsyncresult.md) <br/> |
|Interface identifier:  <br/> |IID_IOSTX  <br/> |
   
## Vtable order

|Property |Value |
|:-----|:-----|
|[GetLastError](iostx-getlasterror.md) <br/> |Gets extended information about the last error. |
|[InitSync](iostx-initsync.md) <br/> |Informs the local store that synchronization is about to start. |
|[SyncBeg](iostx-syncbeg.md) <br/> |Prepares the local store for synchronization in a particular state and retrieves the necessary information to replicate. |
|[SyncEnd](iostx-syncend.md) <br/> |Ends synchronization in the current state and exits that state. |
|[SyncHdrBeg](iostx-synchdrbeg.md) <br/> |Starts synchronization for a message header. |
|[SyncHdrEnd](iostx-synchdrend.md) <br/> |Ends synchronization for a message header. |
|[SetSyncResult](iostx-setsyncresult.md) <br/> |Sets the result of the synchronization. |
| *Placeholder member*  <br/> | *Not supported or documented.*  <br/> |
   
## Remarks

When a client uploads or synchronizes folders and folder contents on a local store, it moves the local store from one state to another as depicted in the state transition diagram in [About the Replication State Machine](about-the-replication-state-machine.md). The following is the order of events for the client to move the local store from one state to another:
  
1. The client calls **IOSTX::InitSync** to inform the local store that replication is about to start. 
    
2. Depending on the direction of replication and the objects to replicate, the client calls **IOSTX::SyncBeg** to begin replication in the appropriate state. Outlook provides the client the necessary information, and the client performs the replication. 
    
3. The client calls **IOSTX::SetSyncResult** to return the result of the replication. 
    
4. The client calls **IOSTX::SyncEnd** to end the replication, providing Outlook the necessary information for subsequent replication. 
    
In particular, when downloading message items, the client uses **IOSTX::SyncHdrBeg** and **IOSTX::SyncHdrEnd** to update a full message item with the message header on the local store: 
  
1. Upon **IOSTX::SyncHdrBeg**, the local store transitions into the download message header state. Outlook initially provides the client with the current message header on the local store.
    
2. The client downloads a full message item together with the message header.
    
3. Outlook updates the item on the local store with the full message item.
    
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)

