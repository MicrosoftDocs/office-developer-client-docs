---
title: "IXPLogonSubmitMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon.SubmitMessage
api_type:
- COM
ms.assetid: a261ba0d-cb56-4935-b745-1d4bbd0b8b9d
description: "Last modified: July 23, 2011"
---

# IXPLogon::SubmitMessage

  
  
**Applies to**: Outlook 
  
Indicates that the MAPI spooler has a message for the transport provider to deliver.
  
```
HRESULT SubmitMessage(
  ULONG ulFlags,
  LPMESSAGE lpMessage,
  ULONG FAR * lpulMsgRef,
  ULONG FAR * lpulReturnParm
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how the message is submitted. The following flag can be set:
    
BEGIN_DEFERRED 
  
> The MAPI spooler is calling a transport provider with a message that was previously deferred. The entry identifier of the message is the same as when it was deferred. The message was deferred by passing its entry identifier back to the MAPI spooler by using the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method with the NOTIFY_SENTDEFERRED flag. 
    
 _lpMessage_
  
> [in] A pointer to a message object (representing the message to deliver) that has read/write permission, which the transport provider uses to access and manipulate that message. This object remains valid until after the transport provider returns from a subsequent call to the [IXPLogon::EndMessage](ixplogon-endmessage.md) method. 
    
 _lpulMsgRef_
  
> [out] A pointer to a variable in which the transport provider returns the reference value it assigned to this message. The MAPI spooler passes this reference value in subsequent calls for this message. The MAPI spooler initializes the value to 0 before returning it to the transport provider.
    
 _lpulReturnParm_
  
> [out] A pointer to a variable that corresponds to the MAPI_E_WAIT or MAPI_E_NETWORK_ERROR error value returned by **SubmitMessage**.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BUSY 
  
> The transport provider cannot handle the message, because it is performing another operation. A provider should use this return value to indicate that no processing occurred and that the MAPI spooler should not call **EndMessage**. The MAPI spooler will try the **SubmitMessage** call again later. 
    
MAPI_E_CANCEL 
  
> Although the transport provider requested that the MAPI spooler resubmit the message on a previous **SpoolerNotify** call, conditions have since changed, and the message should not be resent. The MAPI spooler will go on to handle something else. 
    
MAPI_E_NETWORK_ERROR 
  
> A network error prevented successful completion of the operation. The  _lpulReturnParm_ parameter should be set to the number of seconds that will elapse before the MAPI spooler resubmits the message. 
    
MAPI_E_NOT_ME 
  
> The transport provider cannot handle this message. The MAPI spooler should try to find another transport provider for it. A provider should use this return value to indicate that no processing occurred and that the MAPI spooler should not call **EndMessage**.
    
MAPI_E_WAIT 
  
> A temporary problem prevents the transport provider from handling the message. The  _lpulReturnParm_ parameter should be set to the number of seconds that will elapse before the MAPI spooler resubmits the message. 
    
## Remarks

The MAPI spooler calls the **IXPLogon::SubmitMessage** method when it has a message for the transport provider to deliver. The message is passed to the transport provider by using the  _lpMessage_ parameter. 
  
If the provider is ready to accept the message, it should return a reference value by using the  _lpulMsgRef_ parameter, process the passed object, and return the appropriate value (usually S_OK). If the provider is not prepared to handle the transfer, it should return an error value and, optionally, another MAPI return value in  _lpulReturnParm_ to indicate how long the MAPI spooler should wait before resubmitting the message. 
  
A transport provider's implementation of this method can do the following:
  
- Put the message into an internal queue to wait for transmission, possibly copying the message to local storage, and return.
    
- Attempt to perform the actual transmission and return when the transmission completes, either successfully or unsuccessfully.
    
- Determine whether to send the message after checking the resource involved. In this case, if the resource is free, the provider can lock the resource, prepare the message, and submit it. If the resource is busy, the provider can prepare the message and defer sending to a later time.
    
The preferred technique for message transmission depends on the transport provider and the expected number of processes competing for system resources. 
  
During a **SubmitMessage** call, the transport provider controls the transfer of message data from the message object. However, the transport provider should assign a reference value to the message, to which it returns a pointer in  _lpulMsgRef_, before transferring data. It does so because at any point during the process, the MAPI spooler can call the [IXPLogon::TransportNotify](ixplogon-transportnotify.md) method with the NOTIFY_CANCEL_MESSAGE flag set to signal the provider that it should release any open objects and stop message transfer. 
  
The transport provider should not send any nontransmittable properties of the message. When it finds such a property, it should go on to process the next property. The provider should make every effort not to display MAPI_P1 recipient information as part of the transmitted message content; the provider should use this recipient information only for addressing purposes. MAPI_P1 recipients are internally generated recipients that are used for resending messages; they should not be transmitted. Instead, use the other recipients for transmitting recipient information. The purpose of this arrangement is to permit resend recipients to see the exact same recipient table as the original recipients.
  
During a **SubmitMessage** call, the MAPI spooler processes methods for objects that are opened during the transfer of the message, and it processes any attachments. This processing can take a long time. Transport providers can call the [IMAPISupport::SpoolerYield](imapisupport-spooleryield.md) method for the MAPI spooler frequently during this processing to release CPU time for other system tasks. 
  
All message recipients are visible in the recipient table of the message that the MAPI spooler originally passed. The transport provider should process only those recipients that it can handle — based on entry identifier, address type, or both — and that do not already have their **PR_RESPONSIBILITY** ( [PidTagResponsibility](pidtagresponsibility-canonical-property.md)) property set to TRUE. If **PR_RESPONSIBILITY** is already set to TRUE, another transport provider has handled that recipient. When the provider completes sufficient processing of a recipient to determine whether it can handle messages for that recipient, it should set that recipient's **PR_RESPONSIBILITY** property to TRUE in the passed message. Usually, the provider makes this determination after message delivery is complete. 
  
Typically, the transport provider does not return from a **SubmitMessage** call until it completes the transfer of message data. If no error is returned, the next call from the MAPI spooler to the provider is a call to the [IXPLogon::EndMessage](ixplogon-endmessage.md) method. 
  
If **SubmitMessage** returns an error, the MAPI spooler releases the message in process without saving changes. If the transport provider requires message changes to be saved, it must call the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method on the message before returning. 
  
In case of errors that occur because of transport problems, the MAPI spooler retains the message, but it delays resubmitting the message to the transport provider based on the value returned in  _lpulReturnParm_. The transport provider must fill in that value if its return value from **SubmitMessage** is MAPI_E_WAIT or MAPI_E_NETWORK_ERROR. If a severe error condition occurs, the transport provider must call the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method with the NOTIFY_CRITICAL_ERROR flag. 
  
## See also

#### Reference

[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md)
  
[IMAPISupport::SpoolerYield](imapisupport-spooleryield.md)
  
[IXPLogon::EndMessage](ixplogon-endmessage.md)
  
[IXPLogon::TransportNotify](ixplogon-transportnotify.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

