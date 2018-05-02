---
title: "IXPLogon  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon
api_type:
- COM
ms.assetid: 4d24ecaf-11d0-4362-8207-be3407736d7b
description: "Last modified: March 09, 2015"
---

# IXPLogon : IUnknown

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Gives the MAPI spooler access to a transport provider. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Transport logon objects  <br/> |
|Implemented by:  <br/> |Transport providers  <br/> |
|Called by:  <br/> |The MAPI spooler  <br/> |
|Interface identifier:  <br/> |IID_IXPLogon  <br/> |
|Pointer type:  <br/> |LXPLOGON  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[AddressTypes](ixplogon-addresstypes.md) <br/> |Returns the types of recipients that the transport provider handles.  <br/> |
|**RegisterOptions** <br/> | *Not supported or documented.*  <br/> |
|[TransportNotify](ixplogon-transportnotify.md) <br/> |Signals the occurrence of an event about which the transport provider requested notification.  <br/> |
|[Idle](ixplogon-idle.md) <br/> |Indicates that the system is idle, enabling the transport provider to perform low-priority operations.  <br/> |
|[TransportLogoff](ixplogon-transportlogoff.md) <br/> |Initiates the logoff process.  <br/> |
|[SubmitMessage](ixplogon-submitmessage.md) <br/> |Indicates that the MAPI spooler has a message for the transport provider to deliver.  <br/> |
|[EndMessage](ixplogon-endmessage.md) <br/> |Informs the transport provider that the MAPI spooler completed its processing on an outbound message.  <br/> |
|[Poll](ixplogon-poll.md) <br/> |Indicates whether the transport provider has received one or more inbound messages.  <br/> |
|[StartMessage](ixplogon-startmessage.md) <br/> |Initiates the transfer of an inbound message from the transport provider to the MAPI spooler.  <br/> |
|[OpenStatusEntry](ixplogon-openstatusentry.md) <br/> |Opens the transport provider's status object.  <br/> |
|[ValidateState](ixplogon-validatestate.md) <br/> |Checks the transport provider's external status.  <br/> |
|[FlushQueues](ixplogon-flushqueues.md) <br/> |Requests that the transport provider immediately deliver all pending inbound or outbound messages.  <br/> |
   
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

