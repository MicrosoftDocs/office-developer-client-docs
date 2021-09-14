---
title: "Shutting Down a Service Provider"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: e518830b-0aaa-4ce4-a85a-07e4f00750a9
description: "Last modified: December 07, 2015"
 
 
---

# Shutting Down a Service Provider

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When a client calls the [IMAPISession::Logoff](imapisession-logoff.md) method to end the session and shut down all active service providers, MAPI in turn calls the following methods: 
  
- [IABLogon::Logoff](iablogon-logoff.md) for address book providers. 
    
- [IMSLogon::Logoff](imslogon-logoff.md) for message store providers. 
    
- [IXPLogon::TransportLogoff](ixplogon-transportlogoff.md) for transport providers. 
    
These methods have similar implementations. The main tasks that a logoff method performs are as follows:
  
- Releasing all open objects, including subobjects and status objects.
    
- Calling the support object's [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method to decrement its reference count. 
    
- Removing all of your provider's registered [MAPIUID](mapiuid.md) structures. 
    
- Removing your provider's row in the status table.
    
- Performing any tasks that relate to cleaning up resources, such as the following:
    
  - Terminating a connection with a remote server.
    
  - Decrementing the reference count on the logon object.
    
  - Removing the logon object from the list of logon objects that your provider stores.
    
  - In debug mode, issuing traces to locate objects that have leaked memory.
    
When your logoff method returns, MAPI calls the following:
  
- Your logon object's **IUnknown::Release** method. 
    
- Your provider object's **Shutdown** method to perform any final cleanup tasks. Depending on the type of your provider, one of the following methods is called: 
    
  - [IABProvider::Shutdown](iabprovider-shutdown.md) for address book providers 
    
  - [IMSProvider::Shutdown](imsprovider-shutdown.md) for message store providers 
    
  - [IXPProvider::Shutdown](ixpprovider-shutdown.md) for transport providers 
    
- Your provider object's **IUnknown::Release** method. 
    
If your provider is a message store, a client call to [IMsgStore::StoreLogoff](imsgstore-storelogoff.md) will also initiate the shutdown process. **StoreLogoff** shuts down one particular message store provider and has no effect on the session. Only a message store provider can be shut down with this method; there is no explicit way to shut down a particular address book or transport provider. For information about how to respond to a **StoreLogoff** call, see [Shutting Down a Message Store Provider](shutting-down-a-message-store-provider.md).
  
Your provider's DLL will be unloaded when MAPI calls the Win32 API function **FreeLibrary**, a call that is made after the last active client has called [MAPIUninitialize](mapiuninitialize.md). By this time, your service provider will have finished shutting down. 
  
## See also



[MAPI Service Providers](mapi-service-providers.md)

