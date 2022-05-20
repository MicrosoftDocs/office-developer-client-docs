---
title: "Upload Read Status State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 4d45574e-df87-8c44-4aa7-d41b38406f0a
description: "Last modified: March 09, 2015"
 
 
---

# Upload Read Status State

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 This topic describes what happens during the upload read status state of the replication state machine. 
  
## Quick info

|Property |Value |
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_UPLOAD_MESSAGE_READ** <br/> |
|Related Data Structure:  <br/> |**[UPREAD](upread.md)** <br/> |
|From this state:  <br/> |[Upload table state](upload-table-state.md) <br/> |
|To this state:  <br/> |Upload table state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

This state initiates uploading the read status of items in a folder specified in a preceding upload table state. During this state, Outlook initializes the associated **UPREAD** data structure with information for those items in the folder whose read status has changed. The client then updates the read status of these items on the server as being read or unread. 
  
When this state ends, Outlook clears the internal information about the item's read status, preventing the item's read status from being uploaded again. The local store returns to the upload table state.
  
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

