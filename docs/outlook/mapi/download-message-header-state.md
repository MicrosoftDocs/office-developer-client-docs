---
title: "Download Message Header State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 03f69592-a5ea-e30b-9674-9cfa895163d8
description: "Last modified: March 09, 2015"
 
 
---

# Download Message Header State

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 This topic describes what happens during the download message header state of the replication state machine. 
  
## Quick info

|Property |Value |
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_DOWNLOAD_HEADER** <br/> |
|Related Data Structure:  <br/> |**[HDRSYNC](hdrsync.md)** <br/> |
|From this state:  <br/> |[Idle state](idle-state.md) <br/> |
|To this state:  <br/> |Idle state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

During this state, the client updates the header of a message on a local store. The local store enters this state upon **[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)** and exits when **[IOSTX::SyncHdrEnd](iostx-synchdrend.md)** is called. During this state, Outlook initializes members of the associated **HDRSYNC** data structure with information about the header of a message. The client first downloads the full message item from the server and then updates the header of the message item locally. 
  
When syncrhonization ends, the client sets the download results. The local store returns to the idle state.
  
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

