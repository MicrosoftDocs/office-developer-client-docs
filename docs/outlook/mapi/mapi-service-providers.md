---
title: "MAPI Service Providers"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6511e1b5-697e-4ed1-80af-aa8ca56fd045
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Service Providers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are three common types of service providers:
  
- Address book providers.
    
- Message store providers.
    
- Transport providers.
    
Address book and message store providers have many similarities. They register a unique identifier with MAPI that they use for constructing entry identifiers for their objects. They provide a hierarchy of objects and properties that clients can access and manipulate. For their container objects, they support a hierarchy table and a contents table. They support event notification on these tables and optionally on individual objects so that clients can be informed of changes that occur during the session. When operations become lengthy, they can display a progress indicator to inform the user of the operation's status. Clients can communicate with address book and message store providers either indirectly through MAPI by using the [IAddrBook : IMAPIProp](iaddrbookimapiprop.md) and [IMAPISession : IUnknown](imapisessioniunknown.md) interfaces or directly by using one of the service provider interfaces in the following table. 
  
|**Address book provider interfaces**|**Message store provider interfaces**|
|:-----|:-----|
|[IABContainer : IMAPIContainer](iabcontainerimapicontainer.md) <br/> |[IMsgStore : IMAPIProp](imsgstoreimapiprop.md) <br/> |
|[IDistList : IMAPIContainer](idistlistimapicontainer.md) <br/> |[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md) <br/> |
|[IMailUser : IMAPIProp](imailuserimapiprop.md) <br/> |[IMessage : IMAPIProp](imessageimapiprop.md) <br/> |
| <br/> |[IAttach : IMAPIProp](iattachimapiprop.md) <br/> |
   
Transport providers differ from address book and message store providers in the way they communicate with MAPI and with clients. Transport providers typically wait for MAPI to prompt them for information rather than initiate communication. Unlike the other providers, transport providers do not support a variety of objects and tables that are commonly accessed by clients. However, they do support a status object, as do all service providers, and publish its properties in the status table. Whereas address book and message store providers call the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method to register unique identifiers for constructing their entry identifiers, transport providers call the [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method to register unique identifiers, as well as address types for assuming responsibility for the delivery of particular messages. 
  
Your service provider should have three header files: one public header file and two internal files. Use the public header file for configuration and for documenting properties and their values. Include in one of the internal header files all the necessary public MAPI headers; this header file should be included in all of your service provider source files. Use the other internal file to define resource identifiers.
  
Address book, message store, and transport providers perform the following tasks:
  
- Supply an entry point function. 
    
- Supply a provider and logon object to handle logon and initialization. 
    
- If the provider belongs to a message service, supply a message service entry point function. 
    
- Support configuration by implementing a property sheet.
    
- Implement a status object and support the status table. 
    
- Handle shut down.
    
## See also



[MAPI Concepts](mapi-concepts.md)

