---
title: "IXPLogonEndMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon.EndMessage
api_type:
- COM
ms.assetid: bb29e6a0-7a92-46eb-bbeb-6f2df6ac6d21
description: "Last modified: July 23, 2011"
---

# IXPLogon::EndMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Informs the transport provider that the MAPI spooler completed its processing on an outbound message.
  
```cpp
HRESULT EndMessage(
  ULONG ulMsgRef,
  ULONG FAR * lpulFlags
);
```

## Parameters

 _ulMsgRef_
  
> [in] A message-specific reference value that was obtained in an earlier call to the [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) method. 
    
 _lpulFlags_
  
> [out] A bitmask of flags that indicates to the MAPI spooler what it should do with the message. If no flags are set, the message has been sent. The following flags can be set:
    
END_DONT_RESEND 
  
> The transport provider has all the information it needs about this message for now. When the transport provider requires more information or when it has sent the message, it notifies the MAPI spooler by calling the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method with the NOTIFY_SENTDEFERRED flag and by passing the message's entry identifier. 
    
END_RESEND_LATER 
  
> The transport provider is not sending the message at the current time for reasons that are not error conditions. The transport provider should be called again later to send the message.
    
END_RESEND_NOW 
  
> The transport provider needs to restart the message passed to it in an [IMessage::SubmitMessage](imessage-submitmessage.md) method call. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The MAPI spooler calls the **IXPLogon::EndMessage** method after it completes the processing involved in providing extended delivery or nondelivery information. 
  
Once this call returns, the value in the _ulMsgRef_ parameter is no longer valid for this message. The transport provider can reuse the same value on a future message. 
  
All objects that the transport provider opens during the transfer of a message should be released before the **EndMessage** call returns, with the exception of the message object that the MAPI spooler passes to the transport provider. The message object passed by the MAPI spooler is invalid after the **EndMessage** call. 
  
## See also



[IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md)
  
[IMessage::SubmitMessage](imessage-submitmessage.md)
  
[IXPLogon::SubmitMessage](ixplogon-submitmessage.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

