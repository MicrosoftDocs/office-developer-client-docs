---
title: "Upload Delete Status State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: dee566ad-b46d-1015-4b0b-6c3313060142
description: "This topic describes what happens during the upload delete status state of the replication state machine."
 
 
---

# Upload Delete Status State

**Applies to**: Outlook 2013 | Outlook 2016
  
 This topic describes what happens during the upload delete status state of the replication state machine.
  
## Quick info

|Property |Value |
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_MESSAGE_DEL** <br/> |
|Related Data Structure:  <br/> |**[UPDEL](updel.md)** <br/> |
|From this state:  <br/> |[Upload table state](upload-table-state.md) <br/> |
|To this state:  <br/> |Upload table state  <br/> |

> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter.
  
## Description

This state initiates updating on a server those Outlook items (mail, calendar, contact, task, note, or journal) that have been deleted in a folder on a local store specified in a preceding upload table state. During this state, Outlook initializes members in the associated **UPDEL** data structure with information for the items that have been deleted or moved from the folder.
  
The client then deletes the specified items in the folder on the server. To distinguish items that have been moved as opposed to having been deleted, the client must check the *pupmov* members identified in the **UPDEL** structure.
  
When this state ends, Outlook clears the internal information indicating that the item has been deleted; consequently, Outlook will no longer have a record of the item. The local store returns to the upload table state.
  
## See also

[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)
