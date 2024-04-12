---
title: "IXPLogon  IUnknown"
description: "Describes the properties and vtable order of members for IXPLogon IUnknown, which gives the MAPI spooler access to a transport provider."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon
api_type:
- COM
ms.assetid: 4d24ecaf-11d0-4362-8207-be3407736d7b
---

# IXPLogon : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gives the MAPI spooler access to a transport provider. 
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Transport logon objects  <br/> |
|Implemented by:  <br/> |Transport providers  <br/> |
|Called by:  <br/> |The MAPI spooler  <br/> |
|Interface identifier:  <br/> |IID_IXPLogon  <br/> |
|Pointer type:  <br/> |LXPLOGON  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[AddressTypes](ixplogon-addresstypes.md) <br/> |Returns the types of recipients that the transport provider handles. |
|**RegisterOptions** <br/> | *Not supported or documented.*  <br/> |
|[TransportNotify](ixplogon-transportnotify.md) <br/> |Signals the occurrence of an event about which the transport provider requested notification. |
|[Idle](ixplogon-idle.md) <br/> |Indicates that the system is idle, enabling the transport provider to perform low-priority operations. |
|[TransportLogoff](ixplogon-transportlogoff.md) <br/> |Initiates the logoff process. |
|[SubmitMessage](ixplogon-submitmessage.md) <br/> |Indicates that the MAPI spooler has a message for the transport provider to deliver. |
|[EndMessage](ixplogon-endmessage.md) <br/> |Informs the transport provider that the MAPI spooler completed its processing on an outbound message. |
|[Poll](ixplogon-poll.md) <br/> |Indicates whether the transport provider has received one or more inbound messages. |
|[StartMessage](ixplogon-startmessage.md) <br/> |Initiates the transfer of an inbound message from the transport provider to the MAPI spooler. |
|[OpenStatusEntry](ixplogon-openstatusentry.md) <br/> |Opens the transport provider's status object. |
|[ValidateState](ixplogon-validatestate.md) <br/> |Checks the transport provider's external status. |
|[FlushQueues](ixplogon-flushqueues.md) <br/> |Requests that the transport provider immediately deliver all pending inbound or outbound messages. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

