---
title: "Upload Message State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 7fdc1494-4f40-38bd-d363-144ca70e5906
description: "Last modified: March 09, 2015"
 
 
---

# Upload Message State

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
 This topic describes what happens during the upload message state of the replication state machine. 
  
## Quick Info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_MESSAGE** <br/> |
|Related Data Structure:  <br/> |**[UPMSG](upmsg.md)** <br/> |
|From this state:  <br/> |[Upload table state](upload-table-state.md) <br/> |
|To this state:  <br/> |Upload table state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

This state initiates uploading an Outlook item (mail, calendar, contact, task, note, or journal) that is new or has been moved to the current folder, or that has been modified. Outlook initializes the correpsonding **UPMSG** data structure with the appropriate information for the item as being added, moved, or modified. 
  
If the item has been added or moved, the client then appropriately adds or updates the item on the server. 
  
If the item has been modified, Outlook further specifies in the **UPMSG** data structure whether the modifications are in a message header (in which case the item is the message header), in the item properties, or in the item itself that requires conflict resolution. The client then updates the item on the server. 
  
When the item upload ends, Outlook notes that the message has been uploaded, so that it will not be processed in a subsequent upload. The local store returns to the upload table state.
  
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

