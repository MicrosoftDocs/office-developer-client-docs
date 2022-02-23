---
title: "Synchronize State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 270ff414-514c-b1fc-db48-761bf6de8867
description: "Last modified: March 09, 2015"
 
 
---

# Synchronize State

**Applies to**: Outlook 2013 | Outlook 2016
  
 This topic describes what happens during the synchronize state of the replication state machine.
  
## Quick info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC** <br/> |
|Related Data Structure:  <br/> |**[SYNC](sync.md)** <br/> |
|From this state:  <br/> |[Idle state](idle-state.md) <br/> |
|To this state:  <br/> |[Download hierarchy state](download-hierarchy-state.md), [synchronize contents state](synchronize-contents-state.md), [upload hierarchy state](upload-hierarchy-state.md), or idle state  <br/> |

> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter.
  
## Description

This state initiates synchronization. A local store can transition to an upload or a download state from here. For example, a local store can move to the upload hierarchy state to upload a folder hierarchy to the server, or it can perform a full synchronization by first uploading the hierarchy and then downloading the hierarchy from the server.
  
During this state, Outlook initializes the associated **SYNC** data structure with the path to the local store, so that Outlook sees modifications during other states.
  
The client sets the [in] members of **SYNC**, which tells Outlook how to handle other states. For example, the client can set *ulFlags* to **UPS_UPLOAD_ONLY** and **UPS_THESE_FOLDERS** and *pel* to a list of entry identifiers of the folders to tell Outlook that only these folders will be uploaded. When this state ends, the local store reverts to the idle state.
  
## See also

[About the Replication API](about-the-replication-api.md)  
[MAPI Constants](mapi-constants.md)  
[About the Replication State Machine](about-the-replication-state-machine.md)  
[SYNCSTATE](syncstate.md)
