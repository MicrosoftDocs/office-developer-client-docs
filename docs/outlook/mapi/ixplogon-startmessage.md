---
title: "IXPLogonStartMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon.StartMessage
api_type:
- COM
ms.assetid: 83c349f7-dcac-4268-befe-fb2bc0cd9c50
description: "Last modified: July 23, 2011"
---

# IXPLogon::StartMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initiates the transfer of an inbound message from the transport provider to the MAPI spooler.
  
```cpp
HRESULT StartMessage(
  ULONG ulFlags,
  LPMESSAGE lpMessage,
  ULONG FAR * lpulMsgRef
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpMessage_
  
> [in] A pointer to a message object (representing the inbound message) that has read/write permission, which is used by the transport provider to access and manipulate that message. This object remains valid until after the transport provider returns from the call to **IXPLogon::StartMessage**.
    
 _lpulMsgRef_
  
> [out] A pointer to a reference value assigned to the message. The MAPI spooler initializes this value to 1 before it returns the pointer to the transport provider.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

The MAPI spooler calls the **IXPLogon::StartMessage** method to initiate the transfer of an inbound message from the transport provider to the MAPI spooler. Before the transport provider starts to use the message pointed to by  _lpMessage_, it should store a message reference in the  _lpulMsgRef_ parameter for potential use by a call to the [IXPLogon::TransportNotify](ixplogon-transportnotify.md) method. 
  
During a **StartMessage** call, the MAPI spooler processes methods for objects opened during the transfer of the message, and it also processes any attachments. This processing can take a long time. Transport providers can call the [IMAPISupport::SpoolerYield](imapisupport-spooleryield.md) callback function for the MAPI spooler frequently during this processing to release CPU time for other system tasks. 
  
All recipients in the recipient table that the transport provider creates for the message must contain all required addressing properties. If necessary, the provider can construct a custom recipient to represent a particular recipient. However, if the provider can produce a recipient entry that includes more information, it should do so. For example, if a transport provider has enough information about an address book provider's recipient format that it can build a valid entry identifier for a recipient for that format, it should build the entry identifier.
  
If any nontransmittable properties are received, the transport provider should not store them in the new message. However, the transport provider should store all transmittable properties it receives in the new message.
  
If the incoming message is a delivery report or a nondelivery report and the transport provider is unable to use the [IMAPISupport::StatusRecips](imapisupport-statusrecips.md) method to generate the report from the original message, the provider should itself populate the message with the appropriate properties. However, the transport provider cannot set the message's **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
  
To save the incoming message in the appropriate MAPI message store after processing, the transport provider calls the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. If the transport provider does not have any messages to pass to the MAPI spooler, it can stop the incoming message by returning from the **StartMessage** call without calling **SaveChanges**.
  
All objects that the transport provider opens during a **StartMessage** call should be released before returning. However, the provider should not release the message object that the MAPI spooler originally passed in the  _lpMessage_ parameter. 
  
If **StartMessage** returns an error, the message in process is released without having changes saved and is lost. In this case, the transport provider should pass the NOTIFY_CRITICAL_ERROR flag with a call to the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method and call the [IXPLogon::Poll](ixplogon-poll.md) method to notify the MAPI spooler that it is in a severe error condition. 
  
For more information, see [Interacting with the MAPI Spooler](interacting-with-the-mapi-spooler.md). 
  
## See also



[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md)
  
[IMAPISupport::SpoolerYield](imapisupport-spooleryield.md)
  
[IMAPISupport::StatusRecips](imapisupport-statusrecips.md)
  
[IMessage::GetRecipientTable](imessage-getrecipienttable.md)
  
[IXPLogon::Poll](ixplogon-poll.md)
  
[IXPLogon::TransportNotify](ixplogon-transportnotify.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

