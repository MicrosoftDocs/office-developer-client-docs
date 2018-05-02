---
title: "Interacting with the MAPI Spooler"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 5cc1d0a8-ad23-4173-b220-b7c0169073fa
description: "Last modified: July 23, 2011"
 
 
---

# Interacting with the MAPI Spooler

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The methods in the [IXPLogon : IUnknown](ixplogoniunknown.md) interface are used by the MAPI spooler when calling the transport provider. It should be possible for most types of transport providers to implement most of these methods so that they return quickly. This is desirable because if a method takes a long time to return then it should be broken up with calls back to the MAPI spooler to release the CPU for other tasks. 
  
The MAPI spooler does its work and makes its calls to transport providers when foreground applications are idle. After optionally displaying dialog boxes when the transport provider is first logged on (governed by flags passed from MAPI to the transport provider), transport providers operate in the background unless called by the client to flush send and receive queues. Flushing queues is the only time that a transport provider need not release the CPU, and then only if the user is informed that a potentially long action is in progress. The MAPI spooler typically requests that a transport provider flush its queues in response to a user action, so the transport provider typically does not need to do anything to ensure that the user is informed.
  
A transport provider can independently decide to flush a queue and use the STATUS_INBOUND_FLUSH and STATUS_OUTBOUND_FLUSH bits in the **PR_STATUS_CODE** ( [PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property of its status row to inform the MAPI spooler that it wants attention so that it can get the job done. The status row is updated using the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method. In this case the transport provider should probably display a progress indicator or other interface to inform the user that a long action is occuring. 
  
Since network activity often takes more than 0.2 seconds, transport providers should, whenever possible, use asynchronous network requests. This enables them to initiate a request, release the CPU by calling back to the MAPI spooler, and when the MAPI spooler again gives them control, to check to see if their network request has completed. If it has not yet completed, they again release the CPU by calling back to the MAPI spooler with the [IMAPISupport::SpoolerYield](imapisupport-spooleryield.md) method. 
  
During message processing, between [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) and [IXPLogon::EndMessage](ixplogon-endmessage.md) and during [IXPLogon::StartMessage](ixplogon-startmessage.md), the transport provider typically makes many calls on objects exposed to it by the MAPI spooler. As part of its handling of these objects, the MAPI spooler helps the transport provider behave appropriately as a background process by yielding on its own when appropriate. A transport provider requiring time-critical processing can declare a critical section to the MAPI spooler using the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) support object method. In this case, the CPU is released only on explicit **SpoolerYield** calls by the transport provider until the transport provider ends critical section processing with another call to **SpoolerNotify**.
  
> [!NOTE]
> This is not the same as a Win32 critical section. This should only be done when the transport provider needs real-time control of external resources such as reading incoming data from a fax line. Since this raises the priority of the MAPI spooler process and can cause the workstation to be unresponsive for the duration of the operation, it is a good idea to notify the user that a potentially long action is underway and provide a progress indicator if possible. 
  

