---
title: "Upload Hierarchy State"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: e39c4198-4913-5e86-900a-32e5ba5d801c
description: " This topic describes what happens during the upload hierarchy state of the replication state machine." 
---

# Upload Hierarchy State

**Applies to**: Outlook 2013 | Outlook 2016
  
 This topic describes what happens during the upload hierarchy state of the replication state machine.
  
## Quick info

|Property |Value |
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |
|Related Data Structure:  <br/> |**[UPHIER](uphier.md)** <br/> |
|From this state:  <br/> |[Synchronize state](synchronize-state.md) <br/> |
|To this state:  <br/> |[Upload folder state](upload-folder-state.md), or synchronize state  <br/> |

> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing one state to another must eventually return to the former from the latter.
  
## Description

This state initiates uploading a folder tree hierarchy that has been specified in a preceding synchronize state. Outlook determines the number of folders that have been created or modified in that hierarchy and initializes *cEnt* in **UPHIER**. Outlook also keeps a count of the number of uploaded folders with another member *iEnt*. To upload each of the *cEnt* folders, the client moves the local store into the upload folder state, returning to the upload hierarchy state when the folder upload finishes.
  
When the upload hierarchy state ends, the local store returns to the synchronize state.
  
## See also

[About the Replication API](about-the-replication-api.md)
[MAPI Constants](mapi-constants.md)
[About the Replication State Machine](about-the-replication-state-machine.md)
[SYNCSTATE](syncstate.md)
