---
title: "Transport Provider and MAPI Spooler Operational Model"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: b0f8d8f0-fed7-4a7c-bc40-e935f159591d
 
 
---

# Transport Provider and MAPI Spooler Operational Model

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Transport provider initialization, startup, processing, shutdown and deinitialization are accomplished by a series of calls from the MAPI spooler to the transport provider. The calls are sequenced as follows:
  
1. The MAPI spooler calls the [XPProviderInit](xpproviderinit.md) function, passes a support object, gets the provider object, and checks that the transport provider and MAPI spooler support a compatible range of MAPI version numbers. 
    
2. The MAPI spooler calls the [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) method of the [IXPProvider : IUnknown](ixpprovideriunknown.md) interface. A session is established between the MAPI spooler and the transport provider with the credentials in the current section of the profile. The transport provider returns a logon object. 
    
3. The MAPI spooler calls the [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method. The transport provider returns a list of the unique identifiers (UIDs) and email address types it will accept. 
    
4. The transport provider calls the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method to create its row in the MAPI status table. 
    
5. The MAPI spooler calls the [IXPLogon::TransportNotify](ixplogon-transportnotify.md) method to enable message transmission and reception. 
    
6. If requested by the transport provider in its return for the **TransportLogon** call, the MAPI spooler periodically calls the [IXPLogon::Idle](ixplogon-idle.md) method. Idle processing is useful if the transport provider needs to poll the underlying messaging system for new messages or perform other low-priority tasks. 
    
7. The MAPI spooler and transport provider send and receive messages. For more information, see [Message Submission Model](message-submission-model.md) and [Message Reception Model](message-reception-model.md). The MAPI spooler services transport requests and calls on support, message, and attachment objects.
    
8. The MAPI spooler calls the **TransportNotify** method to disable message transmission and reception. 
    
9. The MAPI spooler releases the logon and provider objects. For more information, see the [IXPProvider::Shutdown](ixpprovider-shutdown.md) method. 
    

