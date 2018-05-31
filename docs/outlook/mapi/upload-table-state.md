---
title: "Upload Table State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: fe167c90-c817-b627-0728-5c6393477c22
description: "Last modified: March 09, 2015"
 
 
---

# Upload Table State

  
  
**Applies to**: Outlook 
  
 This topic describes what happens during the upload table state of the replication state machine. 
  
## Quick info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_TABLE** <br/> |
|Related Data Structure:  <br/> |**[UPTBL](uptbl.md)** <br/> |
|From this state:  <br/> |[Synchronize contents state](synchronize-contents-state.md) <br/> |
|To this state:  <br/> |[Upload message state](upload-message-state.md), [upload delete status state](upload-delete-status-state.md), [upload read status state](upload-read-status-state.md), or synchronize contents state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

This state initiates uploading the contents of a folder that has been specified in a preceding synchronize contents state. The folder can be a mail, calendar, contacts, tasks, notes, or journal folder. During this state, Outlook creates a list of items that have been added, modified, moved, deleted, or marked as read, and prepares the appropriate internal information for the corresponding upload message state, upload delete status state, or upload read status state.
  
When this state ends, Outlook marks the folder as having its contents synchronized, so that the contents will not be uploaded again until another modification is made. The local store returns to the synchronize contents state.
  
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

