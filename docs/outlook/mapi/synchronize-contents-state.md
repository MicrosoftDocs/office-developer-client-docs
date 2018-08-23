---
title: "Synchronize Contents State"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 52216bc3-8cbd-3856-ea46-78f7d0dd66ff
description: "Last modified: March 09, 2015"
 
 
---

# Synchronize Contents State

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 This topic describes what happens during the synchronize contents state of the replication state machine. 
  
## Quick info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_CONTENTS** <br/> |
|Related Data Structure:  <br/> |**[SYNCCONT](synccont.md)** <br/> |
|From this state:  <br/> |[Synchronize state](synchronize-state.md) <br/> |
|To this state:  <br/> |[Download table state](download-table-state.md), [upload table state](upload-table-state.md), or synchronize state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

This state initiates one of the two replication processes: uploading the contents of specified folders on a local store, or a full synchronization. In a full synchronization, for each of the specified folders, contents are uploaded first and then downloaded. Depending on the  *ulFlags*  set in the corresponding **[SYNC](sync.md)** structure in the preceding synchronize state, Outlook initializes [out] members in the **SYNCCONT** structure to provide information about the contents. 
  
Through the same **SYNCCONT** structure, the client obtains the count of the folders that have content to be uploaded or downloaded. The client will loop through each of these folders by moving the local store to the upload table state to upload a folder, or moving the local store to the download table state to download the folder. 
  
In addition, the client obtains entry IDs for the folders requiring replication.
  
When this state ends, Outlook cleans up its internal information. The local store returns to the synchronize state.
  
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

