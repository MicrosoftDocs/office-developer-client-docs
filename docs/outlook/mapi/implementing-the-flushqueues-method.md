---
title: "Implementing the FlushQueues Method"
description: "The MAPI spooler uses the IXPLogon FlushQueues method to download and upload any pending messages to and from a transport provider."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 8719f8aa-a537-4253-b67d-c4d38c40472b
 
 
---

# Implementing the FlushQueues Method

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPI spooler uses the [IXPLogon::FlushQueues](ixplogon-flushqueues.md) method to download and upload any pending messages to and from a transport provider. Typically, the MAPI spooler will flush the queues for all transport providers that are logged on to the session, starting with the first transport provider as set in the transport order section of the user's profile. Flushing queues is almost always the result of a direct request by the user, so the sending and receiving of messages while queues are flushing is synchronous to the MAPI spooler. Because these calls are synchronous, the transport provider should process them as quickly as possible. 
  
Transport providers must handle the **FlushQueues** call as described in the following sequence of steps to enable proper message processing and to enable external resources such as modems to be used by other transport providers as part of the MAPI spooler's **FlushQueues** operation. 
  
|**Step**|**Component**|**Implementation**|
|:-----|:-----|:-----|
|1. |MAPI spooler  <br/> |Calls the **FlushQueues** method for the first transport provider listed in the transport order of the user's profile, passing the requested flags in the _ulFlags_ parameter. **FlushQueues** is called once with all flags set for the entire upload and download operation. |
|2. |Transport Provider  <br/> |Needs to do a number of things before returning from the **FlushQueues** call. If previously submitted messages are being deferred, the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method should be called with the NOTIFY_SENT_DEFERRED flag set. Note that it is possible for the MAPI spooler to cancel a message that has been deferred before the transport provider has a chance to finish processing the message. If the transport provider uses an external resource such as a modem, the connection to the external resource should be established. The STATUS_OUTBOUND_FLUSH bit in the **PR_STATUS_CODE** ([PidTagStatusCode](pidtagstatuscode-canonical-property.md)) property of the transport provider's status row must be set using the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method. The transport provider should then return S_OK for the **FlushQueues** call. |
|3. |MAPI spooler  <br/> |Checks the transport provider's status row for the STATUS_OUTBOUND_FLUSH bit and calls [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) for the first message in the queue. |
|4. |Transport provider  <br/> |Handles the message and returns from the **SubmitMessage** call. |
|5. |MAPI spooler  <br/> |If the transport provider returns S_OK from **SubmitMessage**, the MAPI spooler calls [IXPLogon::EndMessage](ixplogon-endmessage.md) for the message as it does with regular message sending. If the transport provider returns a value other than S_OK from **SubmitMessage**, the MAPI spooler handles the value appropriately before calling **EndMessage**, or before calling **SubmitMessage** again. |
|6. |Transport provider  <br/> |Returns from **EndMessage** with its message processing status in the _lpulFlags_ parameter. |
|7. |MAPI spooler and transport provider  <br/> |The **SubmitMessage**- **EndMessage** loop continues until all messages in the queue have been downloaded. |
|8. |MAPI spooler  <br/> |Notifies the transport provider that it has finished downloading messages by calling the transport provider's [IXPLogon::TransportNotify](ixplogon-transportnotify.md) method with the NOTIFY_END_OUTBOUND_FLUSH flag set. |
|9. |Transport provider  <br/> |Frees any external resources used in sending outbound messages so they can be used by other transport providers to flush their queues. The STATUS_INBOUND_FLUSH bit in the **PR_STATUS_CODE** property of the transport provider's status row must be set using **ModifyStatusRow**. |
|10. |MAPI spooler  <br/> |Checks the transport provider's status row for the STATUS_INBOUND_FLUSH bit and calls [IXPLogon::StartMessage](ixplogon-startmessage.md) if it is set. |
|11. |Transport provider  <br/> |Processes the message and returns from **StartMessage**. If the transport provider has other messages to upload, it should call **SpoolerNotify** with the NOTIFY_NEWMAIL flag set. If the transport provider has no messages to upload, it should call [IMAPIProp::SaveChanges](imapiprop-savechanges.md) on the message the MAPI spooler passed in **StartMessage** and return. |
|12. |MAPI spooler  <br/> |Continues calling **StartMessage** until **SaveChanges** is called on a message. After the transport provider has finished uploading, the MAPI spooler calls **TransportNotify** with the NOTIFY_END_INBOUND_FLUSH flag set. |
|13. |Transport provider  <br/> |Clears the STATUS_INBOUND_FLUSH bit in the **PR_STATUS_CODE** property of its status row using **ModifyStatusRow** and releases all external resources so they are available for use by other transport providers. |
|14. |MAPI spooler  <br/> |Calls **FlushQueues** for the next transport provider listed in the transport order of the user's profile. |
   
If a client application calls [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) on a transport provider's status object, the transport provider should set the appropriate bit in its status row with **ModifyStatusRow**. The MAPI spooler then calls the transport provider's **IXPLogon::FlushQueues** method at the MAPI spooler's convenience. When the transport provider's **IXPLogon::FlushQueues** method is called as a result of a client application's **IMAPIStatus::FlushQueues** call, the operation occurs asynchronously to the client application. Otherwise **IXPLogon::FlushQueues** works synchronously with the MAPI spooler. 
  
For performance reasons, the MAPI spooler will only call a transport provider's **FlushQueues** method if the STATUS_INBOUND_FLUSH and STATUS_OUTBOUND_FLUSH flags are set in the transport provider's status row. Consequently, a transport provider can stop the **FlushQueues** operation at any time by clearing the STATUS_OUTBOUND_FLUSH and STATUS_INBOUND_FLUSH flags in its status row. If the MAPI spooler is shutting down and needs to end the **FlushQueues** operation, it calls **TransportNotify** with both the NOTIFY_END_INBOUND_FLUSH and NOTIFY_END_OUTBOUND_FLUSH flags set. The transport provider should release all external resources and return. 
  

