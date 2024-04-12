---
title: "Upload Folder State"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 270b1df0-c5cd-0d0f-7b57-2726dee978ab
description: "This topic describes what happens during the upload folder state of the replication state machine."
 
 
---

# Upload Folder State

**Applies to**: Outlook 2013 | Outlook 2016
  
 This topic describes what happens during the upload folder state of the replication state machine.
  
## Quick info

|Property |Value |
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |
|Related Data Structure:  <br/> |**[UPFLD](upfld.md)** <br/> |
|From this state:  <br/> |[Upload hierarchy state](upload-hierarchy-state.md) <br/> |
|To this state:  <br/> |Upload hierarchy state  <br/> |

> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter.
  
## Description

This state initiates uploading a folder in a hierarchy that has been specified in a preceding upload hierarchy state. During this state, Outlook provides the folder object (if it has not been deleted) and the flags indicating the state of the folder (new, moved, modified, or deleted) as part of the corresponding **UPFLD** data structure. The client then uploads this information to the server.
  
If the upload is successful, the client sets *ulFlags* in **UPFLD** to **UPF_OK**. Outlook then clears its internal information about the request to upload the folder.
  
When the folder upload ends, the local store returns to the upload hierarchy state. Based on the **[UPHIER](uphier.md)** structure corresponding to the preceding upload hierarchy state, Outlook determines whether to proceed with uploading the next folder and to prepare for the next upload folder state.
  
> [!NOTE]
> If the client needs to upload only one folder, the client can initiate the replication through the [synchronize state](synchronize-state.md) without entering the upload hierarchy state. The client sets certain members of **[SYNC](sync.md)** — *ulFlags* to **UPS_UPLOAD_ONLY** and **UPS_ONE_FOLDER** and *feid* to the folder's ID — to tell Outlook that only one folder will be uploaded.
  
## See also

[About the Replication API](about-the-replication-api.md)  
[MAPI Constants](mapi-constants.md)  
[About the Replication State Machine](about-the-replication-state-machine.md)  
[SYNCSTATE](syncstate.md)
