---
title: "IXPLogonTransportNotify"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon.TransportNotify
api_type:
- COM
ms.assetid: c712fc17-f436-41cf-9aa3-186c9a86d56e
description: "Last modified: July 23, 2011"
---

# IXPLogon::TransportNotify

  
  
**Applies to**: Outlook 
  
Signals the occurrence of an event about which the transport provider requested notification.
  
```
HRESULT TransportNotify(
  ULONG FAR * lpulFlags,
  LPVOID FAR * lppvData
);
```

## Parameters

 _lpulFlags_
  
> [in, out] A bitmask of flags that signals notification events. The following flags can be set by the MAPI spooler on input and must be returned unchanged on output:
    
NOTIFY_ABORT_DEFERRED 
  
> Notifies the transport provider that a message for which it accepted responsibility is being deferred. Only transport providers that support deferral must support this flag. The  _lppvData_ parameter points to the entry identifier of the canceled message. Messages that the MAPI spooler has not processed can still be deferred by calling the [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md) method. 
    
NOTIFY_BEGIN_INBOUND 
  
> The MAPI spooler can now accept inbound messages for this transport provider session. The MAPI spooler regularly calls the [IXPLogon::Poll](ixplogon-poll.md) method if the transport provider set the LOGON_SP_POLL flag with the [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) call at logon. Once the NOTIFY_BEGIN_INBOUND flag is set, the MAPI spooler honors the NOTIFY_NEWMAIL flag passed in the call to the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method. The status table row for the transport provider session should be updated before returning by calling the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method. The NOTIFY_BEGIN_INBOUND and NOTIFY_END_INBOUND flags are mutually exclusive. 
    
NOTIFY_BEGIN_INBOUND_FLUSH 
  
> Signals the transport provider to cycle through inbound messages as quickly as possible. To comply with this notification, the transport provider should set the STATUS_INBOUND_FLUSH flag in the **PR_STATUS_CODE** ( [PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property of its status table row as soon as it can, by using **ModifyStatusRow**. An inbound messaging cycle is complete when the provider determines it has downloaded all it can, or when it has received a **TransportNotify** method call with the NOTIFY_END_INBOUND_FLUSH flag set. Until the end of the inbound messaging cycle, the provider should not call the [IMAPISupport::SpoolerYield](imapisupport-spooleryield.md) method or otherwise relinquish cycles to the operating system to speed delivery of incoming messages. This is acceptable because the MAPI spooler typically uses NOTIFY_BEGIN_INBOUND_FLUSH only in response to a user's request, via a client application, to deliver all messages now. At the end of the inbound flush operation, the provider should use **SpoolerNotify** to clear the STATUS_INBOUND_FLUSH flag in the **PR_STATUS_CODE** property of its status row. 
    
NOTIFY_BEGIN_OUTBOUND 
  
> Outbound operations can now occur for this transport provider session. If there are any messages to be sent for this provider, a call to the [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) method follows. The status table row for this session should be updated before returning. The NOTIFY_BEGIN_OUTBOUND and NOTIFY_END_OUTBOUND flags are mutually exclusive. 
    
NOTIFY_BEGIN_OUTBOUND_FLUSH 
  
> Works similarly to the NOTIFY_BEGIN_INBOUND_FLUSH flag, but refers to outbound messages. The appropriate status flag is STATUS_OUTBOUND_FLUSH.
    
NOTIFY_CANCEL_MESSAGE 
  
> The MAPI spooler must cancel transfer of the message for which the  _lppvData_ parameter points to the 32-bit value from the **IXPLogon::SubmitMessage** method call. The NOTIFY_CANCEL_MESSAGE flag can be set without the transport provider having returned from the **SubmitMessage**, **IXPLogon::StartMessage**, or **IXPLogon::EndMessage** method call that is associated with the message. The transport provider must return as soon as possible from the entry point that is handling the canceled message. For an inbound message that is currently being processed, the transport provider should save the incoming message wherever it is presently stored and deliver it again at the next convenient time. The message object data already stored for the incoming message is discarded. If the transport provider did not update this 32-bit value at the **StartMessage** or **SubmitMessage** time, the value is 0 for outbound messages and 1 for inbound messages. 
    
NOTIFY_END_INBOUND 
  
> Inbound operations must cease for this transport provider session. The MAPI spooler ceases to use the **Poll** method and ignores NOTIFY_NEWMAIL for this session. In-process messages should be completed. The status table row for the transport session should be updated by calling [ModifyStatusRow](imapisupport-modifystatusrow.md) before returning. The NOTIFY_END_INBOUND and NOTIFY_BEGIN_INBOUND flags are mutually exclusive. 
    
NOTIFY_END_INBOUND_FLUSH 
  
> Notifies the transport provider to come out of inbound flush mode. The transport provider should not stop downloading, but downloading should be done in the background. The status table row for the transport session should be updated by calling **ModifyStatusRow** when the transport provider can comply with this notification. 
    
NOTIFY_END_OUTBOUND 
  
> Outbound operations must cease for this transport provider session. The MAPI spooler ceases to call **SubmitMessage** and ignores the **SpoolerNotify** NOTIFY_READYTOSEND flag. If there is an outbound message currently being sent, it should not be stopped; to stop delivery of a message, use the NOTIFY_CANCEL_MESSAGE flag. The status table row for this session should be updated by calling **ModifyStatusRow** before returning. The NOTIFY_END_INBOUND and NOTIFY_BEGIN_OUTBOUND flags are mutually exclusive. 
    
NOTIFY_END_OUTBOUND_FLUSH 
  
> Works similarly to NOTIFY_END_INBOUND_FLUSH, but refers to outbound messages. The appropriate status flag is STATUS_OUTBOUND_FLUSH.
    
 _lppvData_
  
> [out] A pointer to a pointer to event-specific data. For more information about what  _lppvData_ specifies, see the description for the  _lpulFlags_ parameter. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The MAPI spooler calls the **IXPLogon::TransportNotify** method to signal the transport provider about events for which notification has been requested. These events include a MAPI spooler request to cancel a message transfer, the beginning or ending of inbound or outbound transport operations, and the beginning or ending of an operation to clear an inbound or outbound message queue. 
  
When the user tries to cancel a message that the transport provider has previously deferred, the MAPI spooler calls **TransportNotify**, passing in both the NOTIFY_ABORT_DEFERRED and NOTIFY_CANCEL_MESSAGE flags in  _ulFlags_. If the MAPI spooler is logging off and still has messages in the queue, it passes only NOTIFY_ABORT_DEFERRED in  _ulFlags_ when it calls **TransportNotify**.
  
## Notes to Implementers

The provider must synchronize access to its data on this call, because the MAPI spooler can invoke this method from another thread of execution or from a procedure for a different window. This will most likely occur when the MAPI spooler signals the cancellation of a message that the transport provider has started sending.
  
## See also

- [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) 
- [IMAPISupport::SpoolerYield](imapisupport-spooleryield.md) 
- [IMsgStore::AbortSubmit](imsgstore-abortsubmit.md) 
- [IXPLogon::EndMessage](ixplogon-endmessage.md) 
- [IXPLogon::Poll](ixplogon-poll.md)
- [IXPLogon::StartMessage](ixplogon-startmessage.md)
- [IXPLogon::SubmitMessage](ixplogon-submitmessage.md)
- [IXPProvider::TransportLogon](ixpprovider-transportlogon.md)
- [IXPLogon : IUnknown](ixplogoniunknown.md)

