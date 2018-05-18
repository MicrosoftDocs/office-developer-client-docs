---
title: "Download Hierarchy State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 8e0400ba-8530-e6ac-5de8-a62aeec5e10a
description: "Last modified: March 09, 2015"
 
 
---

# Download Hierarchy State

  
  
**Applies to**: Outlook 
  
 This topic describes what happens during the download hierarchy state of the replication state machine. 
  
## Quick info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_DOWNLOAD_HIERARCHY** <br/> |
|Related Data Structure:  <br/> |**[DNHIER](dnhier.md)** <br/> |
|From this state:  <br/> |[Synchronize state](synchronize-state.md) <br/> |
|To this state:  <br/> |Synchronize state  <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

This state initiates downloading a tree hierarchy of folders from a server to the local store. 
  
Outlook initializes the associated **DNHIER** data structure with a pointer to the hierarchy. The client downloads the hierarchy, and inserts new folders or modifications to folders in the local store. The download process adopts Microsoft Exchange Incremental Change Synchronization (ICS). For more information on ICS, see [ICS Evaluation Criteria](http://msdn.microsoft.com/en-us/library/aa579252%28EXCHG.80%29.aspx).
  
When this state ends, the local store returns to the synchronize state.
  
## See also



[About the Replication API](about-the-replication-api.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

