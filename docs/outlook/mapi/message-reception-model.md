---
title: "Message Reception Model"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d85d269e-2251-4399-9159-a2f47a85e3d1
 
 
---

# Message Reception Model

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The transport provider controls whether the MAPI spooler must poll it for incoming mail or whether it performs a call back to the MAPI spooler when new mail arrives. The transport provider sets the SP_LOGON_POLL flag when it returns from [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) to request polling. Otherwise, the transport provider uses [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) when incoming mail is available. After learning that incoming mail is available, the MAPI spooler opens a new message and asks the transport provider to store the received message properties into the message. 
  
This process works as follows:
  
1. Available messages are indicated by either the transport provider calling **IMAPISupport::SpoolerNotify** or by the MAPI spooler calling [IXPLogon::Poll](ixplogon-poll.md).
    
2. The MAPI spooler calls [IXPLogon::StartMessage](ixplogon-startmessage.md) to initiate the process. 
    
3. The transport provider places a reference value in the location referenced in **StartMessage**. These reference values allow the transport provider and the MAPI spooler to keep track of which message is being processed when there are multiple messages to deliver.
    
4. The transport provider stores the message data into the passed [IMessage : IMAPIProp](imessageimapiprop.md) instance. 
    
5. The transport provider calls the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method on the **IMessage** instance and returns from **StartMessage**.
    
6. The MAPI spooler calls [IXPLogon::TransportNotify](ixplogon-transportnotify.md) if it must stop message delivery. 
    
> [!NOTE]
> If a transport provider must deliver a large number of messages and the transport provider is using **IMAPISupport::SpoolerNotify** instead of **IXPLogon::Poll**, care should be taken not to call **SpoolerNotify** too frequently in order not to deprive other transport providers of CPU time. The MAPI spooler does have logic to prevent this from happening, but in general the interval between **SpoolerNotify** calls should be longer than the time it takes your transport provider to process one message. > Also, the MAPI spooler may not process an incoming message immediately. The MAPI spooler may ask the transport provider to perform other tasks before it receives the incoming message. 
  

