---
title: "Idle State"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 46976bea-c6bb-2e37-2e67-4cbccaa03aec
description: "Last modified: March 09, 2015"
 
 
---

# Idle State

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
 This topic describes what happens during the idle state of the replication state machine. 
  
## Quick Info

|||
|:-----|:-----|
|State Identifier:  <br/> |**LR_SYNC_IDLE** <br/> |
|Related Data Structure:  <br/> | *None*  <br/> |
|From this state:  <br/> | *Not applicable*  <br/> |
|To this state:  <br/> |[Synchronize state](synchronize-state.md) <br/> |
   
> [!NOTE]
> The replication state machine is a deterministic state machine. A client departing from one state to another must eventually return to the former from the latter. 
  
## Description

Nothing happens in this state. A local store is in this state before replication is initiated and after replication is complete.
  
## See also

#### Concepts

[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[About the Replication State Machine](about-the-replication-state-machine.md)
  
[SYNCSTATE](syncstate.md)

