---
title: "Handling a Transport Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 60b3e5f4-4a9b-432f-bad4-4284225ab93f
description: "Last modified: July 23, 2011"
 
 
---

# Handling a Transport Provider

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Clients communicate with transport providers through status objects supplied by transport providers and the MAPI spooler. Clients access status objects by calling [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to retrieve the status table. Status objects implement the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface, which has methods for configuring providers, flushing incoming and outgoing message queues, setting passwords, and state validation. For more information about status objects, see [Status Table and Status Objects](status-table-and-status-objects.md).
  
## In This Section

[Sending or Receiving a Message on Demand](sending-or-receiving-a-message-on-demand.md)
  
> Describes how to send or receive a message on demand.
    
[Setting Transport Order](setting-transport-order.md)
  
> Describes how to set transport order.
    
[Reconfiguring a Transport Provider](reconfiguring-a-transport-provider.md)
  
> Describes how to reconfigure a transport provider and what properties are available to set.
    

