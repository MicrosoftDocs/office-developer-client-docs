---
title: "Implementing a Logon Object"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 41e5c88c-d79d-4e9f-81f4-c4365cfaa15d
description: "Last modified: March 09, 2015"
 
 
---

# Implementing a Logon Object

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Every address book, message store, and transport provider instantiates a logon object as part of its implementation of [IABProvider::Logon](iabprovider-logon.md), [IMSProvider::Logon](imsprovider-logon.md), or [IXPProvider::TransportLogon](ixpprovider-transportlogon.md). Logon objects implement methods that help MAPI service client requests. Depending on your type of service provider, your logon object will support one of the following interfaces. 
  
|**Logon object interface**|**Service provider**|
|:-----|:-----|
|[IABLogon : IUnknown](iablogoniunknown.md) <br/> |Address book provider  <br/> |
|[IMSLogon : IUnknown](imslogoniunknown.md) <br/> |Message store provider  <br/> |
|[IXPLogon : IUnknown](ixplogoniunknown.md) <br/> |Transport provider  <br/> |
   
Address book and message store providers implement the following features in their logon objects:
  
- Support for event notification (**Advise** and **Unadvise** methods). For an overview of event notification, see [Event Notification in MAPI](event-notification-in-mapi.md). For more information about supporting notification in your logon object, see [Supporting Event Notification](supporting-event-notification.md). 
    
- Entry identifier comparison (**CompareEntryIDs** method). For general information about entry identifiers, see [MAPI Entry Identifiers](mapi-entry-identifiers.md). For more information about comparing entry identifiers in your logon object's **CompareEntryIDs** method, see [Supporting Object Access and Comparison](supporting-object-access-and-comparison.md).
    
- Access to additional error information (**GetLastError** method). For more information about handling errors in MAPI, see [Error Handling in MAPI](error-handling-in-mapi.md). 
    
- Access to objects implemented by the service provider (**OpenEntry** method). For more information, see [Supporting Object Access and Comparison](supporting-object-access-and-comparison.md).
    
- Access to a status object (**OpenStatusEntry** method). For general information about status objects, see [MAPI Status Objects](mapi-status-objects.md). For specific information about implementing a status object, see [Status Object Implementation](status-object-implementation.md).
    
- A logoff process (**Logoff** method). For more information, see [Shutting Down a Service Provider](shutting-down-a-service-provider.md).
    
If your provider is an address book provider, you will also implement the following methods and associated features:
  
- [IABLogon::GetOneOffTable](iablogon-getoneofftable.md) to provide a listing of the templates that you support for creating new recipients. For more information, see [One-Off Tables](one-off-tables.md) or [Implementing a Provider One-Off Table](implementing-a-provider-one-off-table.md).
    
- [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) to provide access to the implementation of a recipient whose data resides in a host address book provider. For more information, see [Acting as a Foreign Address Book Provider](acting-as-a-foreign-address-book-provider.md). 
    
- [IABLogon::PrepareRecips](iablogon-preparerecips.md) to ensure that the appropriate properties are available for all of the recipients in a recipient list. For more information, see [IABLogon::PrepareRecips](iablogon-preparerecips.md). 
    
A transport provider's logon object, which implements [IXPLogon : IUnknown](ixplogoniunknown.md), is quite different from the logon objects implemented by the other types of service providers. It has only two features in common with the other logon objects: access to a status object through the [IXPLogon::OpenStatusEntry](ixplogon-openstatusentry.md) method and a logoff operation through the [IXPLogon::TransportLogoff](ixplogon-transportlogoff.md) method. Transport providers implement the following unique features in their logon objects: 
  
- Registration for address types ([IXPLogon::AddressTypes](ixplogon-addresstypes.md) method). For more information about registering an address type, see [Transport Provider and MAPI Spooler Operational Model](transport-provider-and-mapi-spooler-operational-model.md).
    
- Control of message transmission ([IXPLogon::StartMessage](ixplogon-startmessage.md), [IXPLogon::EndMessage](ixplogon-endmessage.md), and [IXPLogon::SubmitMessage](ixplogon-submitmessage.md) methods). For more information, see [Message Reception Model](message-reception-model.md), [Interacting with the MAPI Spooler](interacting-with-the-mapi-spooler.md), and [Message Submission Model](message-submission-model.md).
    
- Internal state validation ([IXPLogon::ValidateState](ixplogon-validatestate.md) method). 
    
- Ability to download or upload messages on demand ([IXPLogon::FlushQueues](ixplogon-flushqueues.md) method). For more information, see [Implementing the FlushQueues Method](implementing-the-flushqueues-method.md).
    
- Ability to query for pending messages ([IXPLogon::Poll](ixplogon-poll.md) method). For more information, see [Message Reception Model](message-reception-model.md).
    
- Idle state detection ([IXPLogon::Idle](ixplogon-idle.md) method). 
    
- Interaction with the MAPI spooler ([IXPLogon::TransportNotify](ixplogon-transportnotify.md) method). 
    
## See also



[Implementing Service Provider Logon](implementing-service-provider-logon.md)

